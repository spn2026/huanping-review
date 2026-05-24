---
title: "环评文件智能审核 - Review Prompt"
description: "参数化 prompt：接受 file_path，执行全量审核并输出 JSON、Markdown、注释 PDF。"
inputs:
  - name: file_path
    description: 文件路径或上传附件引用
    required: true
  - name: checks
    description: 审核类型，默认 full
    default: full
  - name: outputs
    description: 输出格式，支持 json, markdown, annotated_pdf
    default: [json, markdown, annotated_pdf]
---

任务说明：
1. 读取输入文档；若为扫描件，先执行 OCR，并在报告中注明使用了 OCR。
2. 执行下列审核（当 checks=full）：
   - 章节完整性与必填项（列出缺失内容及页码）
   - 法规/标准映射：对照常见环评法规，标注可能不符合或未论证之处；如需，使用网络检索列出参考链接
   - 数据验证：检测表格中异常数值、单位不一致、图表与正文不匹配
   - 风险评估：基于证据给出高/中/低风险判定及建议
3. 生成输出：
   - JSON：机器可读的 issues 数组，包含位置（页码/段落）、严重度、修正建议
   - Markdown：面向审查人的摘要与优先级清单
   - 注释 PDF：在原始 PDF 上添加注释（如果可能）或生成可下载的注释版本

返回示例（JSON 摘要）：
{
  "summary": "发现 3 个高优先级问题，主要与生态影响章节缺失相关",
  "issues": [ {"id":"I1","page":12,"severity":"high","detail":"生态影响分析缺失，未提供物种清单"} ]
}

优先按步骤执行；在无法判断法规条款时，标注为“需人工核实”并列出检索到的参考链接。
