# huanping-review

环评文件智能审核技能（huanping-review）

功能：
- 对环评（EIA）文档执行完整性、法规映射、数据验证与风险评估
- 输出结构化 JSON、Markdown 摘要与带注释的 PDF

快速开始：
1. 克隆仓库：
   git clone https://github.com/spn2026/huanping-review.git
2. 在 VS Code 中打开仓库。若要在本地把技能用于 Copilot Chat，可将 .github/skills/huanping-review 下的文件复制到你的用户提示文件夹（示例路径：%USERPROFILE%\\AppData\\Roaming\\Code\\User\\prompts/），或直接在包含该 .github 目录的仓库中使用。
3. 在 Copilot Chat 中调用技能（示例）:
   - 输入: `/huanping-review` 然后上传文档或填入 file_path 参数
   - 选择 checks=full 以及 outputs=[json,markdown,annotated_pdf]

使用示例（Markdown 摘要输出）：
- Summary: 发现 3 个高优先级问题，主要与生态影响章节缺失相关。

示例 JSON 输出片段：
{
  "summary": "生态影响章节不完整",
  "issues": [
    {"id":"I1","page":12,"severity":"high","detail":"生态影响分析缺失，未提供物种清单"}
  ]
}

贡献：欢迎提交 PR 来改进检查规则、增加法规库或改进 OCR/注释工作流。

仓库：https://github.com/spn2026/huanping-review
