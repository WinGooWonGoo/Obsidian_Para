<%*const GEMINI_API_KEY="여기에 당신의 GEMINI_API_KEY"%>

<%*
// 태그 생성 프롬프트
const tag_prompt = `당신은 **정보 아키텍처 전문가**로서, 제공된 문서를 분석하고 내용에 따라 태그를 생성하는 역할을 수행합니다. 당신의 목표는 문서의 핵심 내용을 정확하게 반영하는 태그를 생성하여 문서 분류 및 검색 효율성을 높이는 것입니다.

## 분석 과정
1. 문서를 주의 깊게 읽고 분석합니다.
2. 다음 사항을 고려합니다:
   - 핵심 주제 및 하위 주제
   - 주요 개념 및 테마
   - 문서의 맥락 및 도메인
   - 잠재적 대상 독자
   - 문서 유형 및 목적

## 태깅 규칙
1. 기존 태그:
   - 제공된 목록에서 **문서의 핵심 주제를 가장 잘 나타내거나, 문서에서 빈번하게 언급되는 핵심 개념을 포함하는** 1~5개의 태그를 선택합니다.
   - 기존 태그 목록에서 **정확히 일치하는** 태그만 사용해야 합니다.
   - 각 태그는 문서 내용과 **직접적으로 관련된 핵심 내용을 반영**해야 합니다.

2. 새로운 태그:
   - 1~3개의 새로운 태그를 생성합니다.
   - 형식: #<카테고리> (예: #머신러닝, #자연어처리)
   - **새로운 태그의 카테고리는 문서의 주요 주제, 유형 또는 목적을 가장 잘 반영하는 용어로 결정합니다.**
   - 기존 태그로 포착되지 않는 **문서의 고유한 측면이나 새로운 관점**을 설명해야 합니다.
   - 기존 태그와의 중복을 피하십시오.

## 중요 사항:
- 모든 태그는 # 접두사를 포함해야 합니다.
- 일반적인 태그를 피하고 구체적인 태그를 사용하십시오.
- 일관된 형식을 유지하십시오.
- **출력 형식: 생성된 모든 태그를 쉼표로 구분하여 한 줄로 표시합니다.**

## 예시:

**기존 태그:**
인공지능, 머신러닝, 딥러닝, 자연어처리, 컴퓨터비전, 데이터분석

**문서:**
최근 딥러닝 기술의 발전으로 이미지 인식 분야에서 괄목할 만한 성과들이 보고되고 있다. 특히 컨볼루션 신경망(CNN) 기반의 모델들은 기존 방식 대비 월등한 성능을 보여주며 다양한 산업 분야에 적용되고 있다.

**출력:**
#딥러닝, #컴퓨터비전, #이미지인식`;
%>

<%*
// 태그 정규화 함수
const processTags = async (file, newTags) => {
  const normalizeTags = tags => [...new Set(tags.map(tag => tag.trim()))];
  await tp.app.fileManager.processFrontMatter(file, (frontmatter) => {
    const existingTags = frontmatter?.tags || [];
    frontmatter.tags = normalizeTags([...existingTags, ...newTags]);
  });
};
%>

<%*
// 노트 내용 가져오기
const fileContent = tp.file.content;
const existingTags = tp.file.tags?.length > 0 ? tp.file.tags : null;
%>

<%*
// 태그 생성용 프롬프트 구성
const tagPromptInput = existingTags 
  ? `**기존 태그:**\n${existingTags.join(", ")}\n\n**문서:**\n${fileContent}`
  : `**문서:**\n${fileContent}`;
%>

<%*
// 태그 생성 요청 보내기
const response = await tp.obsidian.requestUrl({
  method: "POST",
  url: "https://generativelanguage.googleapis.com/v1beta/openai/chat/completions",
  contentType: "application/json",
  headers: {
    "Authorization": "Bearer " + GEMINI_API_KEY,
  },
  body: JSON.stringify({
    model: "gemini-2.0-flash-exp",
    messages: [
      { role: "system", content: tag_prompt },
      { role: "user", content: tagPromptInput }
    ]
  })
});

const tags = response.json.choices[0].message.content
  .split(",")
  .map(t => t.trim());
%>

<%*
// 태그 업데이트
const file = tp.config.target_file;
await processTags(file, tags);
%>

<%*
// 태그 생성 시 줄바꿈 정리
const content = tp.file.content;
if (content.startsWith("---")) {
  const cleaned = content.replace(/^(\s*\n){3,}/, "\n\n");
  await app.vault.modify(tp.config.target_file, cleaned);
}
return;
%>
