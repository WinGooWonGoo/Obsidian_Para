# Obsidian MetaData Vault

> ⚠️ 이 저장소는 [테디노트님의 Obsidian Templater](https://github.com/teddylee777/obsidian-templater) 저장소를 기반으로 포크되었습니다.
> 
> 원본 저장소의 템플릿을 비개발자들이나 라이트개발유저들을 위해 수정 및 보완한 버전입니다.

이 저장소는 개인 지식 관리 시스템(PKM)을 위한 옵시디언 볼트입니다.

## 📁 볼트 구조

```
.
├── 1. Personal/        # 예시 파일
├── 2. Relation/        # 예시 파일
├── 3. Career/          # 예시 파일
├── 4. Resource/        # 예시 파일
├── 90. Settings/       # 설정 관련, 탬플릿
├── Index/              # 생성되는 인덱스 저장
└── P.A.R.A/           # 생성되는 P.A.R.A  저장
```

## 🚀 시작하기

1. 이 저장소를 클론합니다:
   ```bash
   git clone [repository-url]
   ```

2. [옵시디언](https://obsidian.md)을 설치합니다.

3. 옵시디언에서 "Open folder as vault"를 선택하고 클론한 폴더를 선택합니다.

## 🔧 설정

- `.obsidian` 폴더는 개인 설정을 위해 .gitignore에 포함되어 있습니다.
- 자신만의 설정으로 옵시디언을 구성하실 수 있습니다.

## 📚 사용 방법

https://anpigon.tistory.com/484
https://www.youtube.com/watch?v=z5Zo6vrYdFk

를 활용했습니다. 커스터마이징을 원하는 분들은 해당 블로그와 유튜브를 활용하면 좋습니다. 안피곤님과 테디노트님 버전에서, PARA Method에 최적화를 시키고, 비개발자들이나 라이트개발유저들을 위해서 바꾼 것입니다. 

개발자 분들이라면 위의 링크을 통해 커스터마이징하는 것이 좋습니다. 사용 방법 또한 비개발자들을 위한 것입니다!

![메타데이터 자동 첨부 예시](img/스크린샷%202025-04-02%20오후%202.29.55.png)

이런 "메타데이터"들을 자동으로 첨부해주는 것인데요. 

![메타데이터 활용 예시](img/스크린샷%202025-04-02%20오후%202.30.48.png)
이것을 미리미리 해둔다면, 나중에 binding을 좀 더 생산성있고, 다양한 용도로 사용하실 수 있습니다. 활용하는 법은 나중에 또 알려드릴게요.

![폴더 구조 예시](img/스크린샷%202025-04-02%20오후%201.55.24.png)

첨부 파일에는 다음과 같은 구조로 짜 있을 겁니다. 왜 PARA method인데, PARA에 맞는 각각의 폴더가 없냐는 의문이 들 수 있습니다.

그 이유는 제가 앞서 언급한 

memo -> binding -> documenting 의 단계의 특성 때문입니다. PARA의 속성은 지속적으로 변화시켜야 하는 속성입니다. 지속적으로 memo-> binding의 단계를 반복적으로 해주어야 하는 것입니다. 

반면, 폴더 구조는 그 자체로 documenting의 속성을 갖고 있습니다. 때문에 P.A.R.A 각 속성은 동적으로 활용할 수 있게 만들었습니다. 폴더구조는 기존 메모앱을 사용하시는 것처럼 사용하시면 됩니다. 파일에는 제가 예시로 넣은 것(1. Personal, 2. Relation, 3. Career, 4. Resource)들이 있습니다. 이 파일들은 지우셔도 되고, 활용하셔도 됩니다.

단, <90. Settings>와 그 부속된 파일들만 건들지 않으시면 됩니다.

### API 설정하기

우선  90. Settings의 91. Templates 밑에 내개의 파일들은 아직 온전한 파일들이 아닙니다. 이탬플릿은 근본적으로 챗봇들에게 메타데이터를 생각하고 설정해달라고 하는 원리이기 때문입니다. 


따라서 챗봇들에게 도움을 받기 위해서는 필요한 게 있습니다. 그것이 바로 API key.이고요. 이 API key는 각자가 설정하는 것이 좋습니다.

https://doldol.kr/114

여기를 참조해서 구글 GEMINI API 키를 생성해주세요! 그리고 나서 발급받은 api 키를 Template 파일들 상단에 모두 첨부해주세요. 반드시 ""안에 넣어야 합니다.

```
<%_*
// OpenAI API 키 설정
const GEMINI_API_KEY="여기에 당신의 GEMINI_API_KEY"
%>
```

## 🧩 옵시디언 필수 플러그인 소개 (feat. 내가 쓰는 플러그인)

옵시디언의 진짜 힘은 플러그인에 있습니다. 직접 활용하시고, 찾아보시면 더 많은 확장된 기능들을 사용하실 수 있습니다. 제 탬플릿은 아래의 플러그인들에 맞춰서 작성되었습니다. 아마 제 첨부파일을 복제하신다면 플러그인들이 자동으로 설치될 수도 있습니다.

하지만 그렇지 않을 수도 있습니다. 우선, 옵시디언의 왼쪽 아래 설정이나, Preferences 버튼을 누르시면 다음과 같은 창이 뜰겁니다. 거기서 Community plugins를 가시면, 플러그인들을 관리하는 화면이 뜹니다. 

여기서 Installed plugins를 보시면 두 개의 플러그인들이 떠야 합니다. "Commander"와 "Templater"입니다. (물론 해당 플러그인들이 없어도 자유롭게 제 파일들을 커스터마이징 하셔서 쓸 수도 있습니다.)

만약 설치되어 있지 않다면, 같은 화면 Community plugins 옆 Browse를 눌러 직접 설치하실 수도 있습니다.

![플러그인 설정 화면](img/스크린샷%202025-04-02%20오후%202.02.23.png)

이 화면에서 플러그인의 설정을 눌러 세부조정하거나, 왼쪽 메뉴 아래 Community plugins 밑에서 해당 플러그인을 누르시면 세부조정할 수 있습니다.

Browse 화면

![플러그인 브라우저 화면](img/스크린샷%202025-04-02%20오후%202.14.20.png)

각 플러그인들에 대해 설명을 드리자면, 

### 1. **Templater (by SilentVoid)**

> **기능**: 템플릿 기능을 고도화 (변수, 날짜 자동삽입, 사용자 입력 등 지원)  
> **활용 예시**: "Daily Note", "미팅 회의록", "독서 기록" 등 반복되는 양식을 자동으로 생성

기본적으로 플러그인을 사용하지 않아도, 탬플릿을 작성하고 탬플릿을 활용할 수 있습니다. 반복되는 작업들을 탬플릿으로 만들어 재사용하는 것입니다. Templater는 그 기능을 용이하게 만들어주는 장치입니다. 설정을 위해 Templater 설정으로 가주세요.

![Templater 설정 화면](img/스크린샷%202025-04-02%20오후%202.16.00.png)

그럼 다음과 같은 화면이 뜰텐데 다음과 같이 설정해주세요. 특히 Template folder location이 제가 드린 파일과 일치하는지 살펴주세요. 만약 새로 탬플릿을 직접 다운받거나 만드시고 활용하신다면, 저기 있는 파일 경로를 설정해주시면 됩니다.

![Templater 폴더 설정](img/스크린샷%202025-04-02%20오후%202.18.06.png)

그리고 아래로 내려 설정을 다음과 같이 해주세요.

![Templater 추가 설정](img/스크린샷%202025-04-02%20오후%202.20.14.png)

그 아래 Hotkey까지 설정해주시면, 

![Templater 단축키 설정](img/스크린샷%202025-04-02%20오후%202.21.00.png)

이제 메모 화면에서 <cmd+P> 혹은 <ctrl+ P>를 눌러 template을 검색하시면 해당 구조를 사용하실 수 있습니다. 아직 하지 마시고 밑으로 내려보세요.

![템플릿 검색 화면](img/스크린샷%202025-04-02%20오후%202.21.53.png)

### 2. **Commander (by jsmorabito & phibr0)**

> **기능**: 명령어를 어디서든 실행할 수 있도록 설정. 커맨드 팔레트 강화 + 매크로 생성  
> **활용 예시**: 자주 사용하는 작업을 매크로로 만들어 한 번에 실행하는 버튼 만들기

하지만 위에 탬플릿을 생성 할 때마다 검색하기 귀찮으실 겁니다. 물론 hotkey를 설정할 수도 있지만 더 편하게 하려면 이 플러그인을 활용하시면 됩니다.

아래 화면처럼 설치한 플러그인 Commander 설정에서 Macros 항목에서 Macro를 추가해주세요.

![Commander 매크로 설정](img/스크린샷%202025-04-02%20오후%203.25.04.png)

그리고 나서, Add Macro들을 누른뒤  template들을 경로에 맞게 설정해주세요.

![Commander 매크로 추가](img/스크린샷%202025-04-02%20오후%203.26.52.png)

이후 Tab Bar에서 Macro에서 설정한 이름으로 커맨더를 추가해주시면,

![Commander 탭바 설정](img/스크린샷%202025-04-02%20오후%203.28.04.png)

이 기능을 사용하게 되면 오른쪽위에 제가 설정한 심장박동 모양의 버튼이 생길것입니다. 심장박동 모양은 제가 설정한거고 여러분들이 자유롭게 설정해주시면 됩니다. 눌러주시면 저절로 탬플릿들을 순차적으로 실행하고, 메타데이터들이 생성됩니다.

![Commander 버튼 예시](img/스크린샷%202025-04-02%20오후%202.07.03.png)

### API 또 다시 확인!!!

중요하기 때문에 다시 강조드립니다.

https://doldol.kr/114

여기를 참조해서 구글 GEMINI API 키를 생성해주세요! 그리고 나서 api 키를 각 Template 상단에 모두 첨부해주세요. 반드시 ""안에 넣어야 합니다.

```
<%_*
// OpenAI API 키 설정
const GEMINI_API_KEY="여기에 당신의 GEMINI_API_KEY"%>
```


### 커스터마이징 하기

안에는 챗봇을 불러와서 프롬프트로 명령을 내리고, 그 데이터를 다시 받는 구조로 만들어져 있습니다.

#### Template-01-BasicSetup
```
<%_*
// 노트 내용
const fileContent = tp.file.content;
_%>

<%_*
// file 가져오기
const noteType = await tp.system.suggester(
    ["[[📌 Project]]", "[[📌 Area]]", "[[📌 Resource]]", "[[📌 Archive]]"], 
    ["[[📌 Project]]", "[[📌 Area]]", "[[📌 Resource]]", "[[📌 Archive]]"], 
    true, 
    "노트 옵션을 선택하세요.");
const file = tp.config.target_file

await tp.app.fileManager.processFrontMatter(file, (frontmatter) => {
  // metadata 업데이트
  frontmatter.created = tp.file.creation_date();
  frontmatter.author = "Won-Goo";
  frontmatter.type = noteType;
  frontmatter.source = "";
});
_%>
```

가장 기본적인 메타데이터 설정입니다. 여기선 챗봇이 필요없어서, API도 필요없어요.

해당 파일엔 다음과 같이 써 있을 텐데요. 여기서 노트타입을 설정하고 있습니다. 만약에 P.A.R.A가 아니라, 다른 설정을 원하시면 [[]] 안에 들어있는 각각의 글자들을 모두 바꿔주시면 돼요. 두개씩 있는데 모두 바꿔주셔야 합니다.

그 밑에는 생성날짜와, 작성자이름을 자동으로 설정되게 해놨고요. author안에 역시 원하시는 이름을 넣어주시면 됩니다. 그리고 source는 나중에 연결할 파일들입니다. 여기에 나무위키처럼 다양한 링크들을 넣을 거예요.

### Index
```
<%_*
// OpenAI API 키 설정
const GEMINI_API_KEY="여기에 당신의 GEMINI_API_KEY"%>

<%_*
// 프롬프트
const index_prompt = `You are an expert in generating an appropriate index properties that will be used in Obsidian Note. Your mission is to generate one or two indexes suitable for given content.
Your generated output must be comma-separated values.

Here is the example output:

### Example Output:

[[🏷️ 스터디]], [[🏷️ Blog]]

Here's a list of possible substitutions for index. You must use one of these indexes listed below.

<Index List>
- [[🏷️ 자기소개서]] : Cover letter or Personal Statement. Mostly
- [[🏷️ 스터디]] : Self studying contents. Mostly development self memo will be this index.
- [[🏷️ Blog]] : Contents used in Blog
- [[🏷️ Research]] : Contents used for Business Research
- [[🏷️ 사이드 프로젝트]] : Contents related to Side Projects
- [[🏷️ 커리어]] : Contents used for Career
- [[🏷️ 데일리 노트]] : Daily note related contents
</Index List>

####

[Note] 
- Write your Final Answer in Korean. 
- DO NOT narrate, just write the output without any markdown formatting of wrapping.
- Generated indexes must be related to the content. Otherwise, you will be penalized.
- Generated indexes must be one of the <Index List>
`
_%>
 ```


여기서는 인덱스를 관리해요. 보시면 아시겠지만, 글의 목표나 형식들을 관리하려고 하고 있어요. 인덱스가 곧 글의 형식일 필요는 없지만, 이런 식으로 관리하시면 편할 겁니다.

여기서, Index List 밑에 있는 것들을 자유롭게 작성해주시면, 원하시는 대로 챗봇이 해줄 수 있습니다. 저 이모티콘은 "[[[[🏷️ 예시 노트]]]] " 여기서 괄호 안에 있는 건 여러분들이 원하시는대로 설정하시면 됩니다. 그 옆에 설명에 챗봇이 잘 알아들을 수 있는 문장으로 만들어 주세요. 

### Template-03-Tag

여기서는 앞서 언급한 Gemini API KEY만 바꿔주셔도 돼요. 

### Template-04-Summary

마찬가지입니다. API KEY만 설정해주세요. 이 기능은 긴글을 스크랩할 때 유용해요. 거슬리는 분들도 있을 겁니다. 만약 그러시다면, 플러그인 관리를 통해서 이기능을 매크로에서 제외 하면 됩니다!


