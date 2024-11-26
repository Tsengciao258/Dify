# DifyPractice
本文档分享了自己制作的一些实用的dify工作流

助理施工机器人：

一、简介
基于 RAG（检索增强生成）技术，通过整合实际工程的施工方案和当地的建筑法规，能够从海量施工数据中快速获取关键信息并生成精准解答。它支持用户通过自然语言交互解决施工管理中的问题，如流程优化、材料计算和技术指导，帮助直观理解施工计划。在知识库中无法检索到答案时，也会使用必应进行网页搜索。该软件具有强大的学习与扩展能力，可根据项目需求进行定制化开发，适用于现场管理、项目决策辅助和员工培训等多种场景，助力施工效率提升和智能化转型。

示例：
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/%E7%A4%BA%E4%BE%8B.png)

二、制作流程

1.创建知识库:

在首页点击知识库，选择创建知识库并选择作为知识库的文本文档。注意：文档支持 TXT、 MARKDOWN、 PDF、 HTML、 XLSX、 XLS、 DOCX、 CSV、 MD、 HTM格式，格式与文件后缀需保持一致，每个文件不超过 15MB。
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/%E7%9F%A5%E8%AF%86%E5%BA%93%E5%88%9B%E5%BB%BA/AAA.png)
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/%E7%9F%A5%E8%AF%86%E5%BA%93%E5%88%9B%E5%BB%BA/BBB.png)

选择文档后，进行知识库的处理，选择合适的索引方式，其中高级索引需要消耗token。然后选择合适的Embedding模型和Rerank模型，推荐选择混合检索。在选择后点击“保存并处理”，等待文件嵌入后即可测试和使用。
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/%E7%9F%A5%E8%AF%86%E5%BA%93%E5%88%9B%E5%BB%BA/ccc.png)
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/%E7%9F%A5%E8%AF%86%E5%BA%93%E5%88%9B%E5%BB%BA/DDD.png)

2.workflow编排

在工作室栏创建新应用。选择知识检索节点，在知识检索中插入知识库和开始中的查询变量。
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/%E7%9F%A5%E8%AF%86%E6%A3%80%E7%B4%A2.png)

随后在插入一个LLM节点进行问题分类，在提示词中要求大语言模型对针对知识库的问题作出特定的回答，以便随后的ifelse路径分叉。
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/%E9%97%AE%E9%A2%98%E5%88%86%E7%B1%BB.png)

在ifelse节点中，接入分类后的路径，并在ifelse节点中选择问题分类产出的上下文进行分类，注意对逻辑的判断。
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/ifelse.png)

最后在不同的路径接入大语言模型和工具节点进行问题的分析和处理，注意提醒用户问题的答案来源，以便用户对答案的可靠性做出判断。
![image](https://github.com/Tsengciao258/Dify-workflow-practice/blob/main/%E6%96%BD%E5%B7%A5%E5%8A%A9%E7%90%86%E9%99%84%E4%BB%B6/final.png)





