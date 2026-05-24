环评文件智能审核技能 — 使用说明

1) 将技能放在仓库的 .github/skills/huanping-review/ 下（已经包含此仓库）。
2) 在 Copilot Chat 中搜索或直接键入技能名称以触发（UI 可能显示为 slash 命令或技能列表）。
3) 参数示例：
   - file_path: 上传文件或给出文件 URL
   - checks: full
   - outputs: [json, markdown, annotated_pdf]

4) 如果想把技能作为个人使用：复制目录下的 .prompt.md 到 VS Code 用户提示文件夹（%USERPROFILE%\\AppData\\Roaming\\Code\\User\\prompts）即可在任意工作区调用。

常见问题：
- 如何发布 GitHub Release：在仓库页面进入 Releases → Draft a new release，输入 tag (v1.0.0) 与说明，点击 Publish release。