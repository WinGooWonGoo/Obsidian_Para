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