---
title: "2025年跨平台桌面AI客户端评测报告：普通用户视角"
date: 2025-06-12T22:05:22+08:00
draft: false
description: "本次评测报告聚焦于七款在2025年备受关注的跨平台桌面AI客户端：cherry-studio、chatbox、HyperChat、lmstudio、deepchat、ChatALL和gpt4all。本报告旨在从普通用户的实际需求出发，对这些客户端进行全面、深入的评估，分析它们在功能特性、性能表现、用户体验、模型支持、隐私安全性、扩展性以及社区活跃度等方面的优劣，最终为普通用户提供一份清晰、实用的选型指南。"

tags: ["AI", "人工智能", "大模型", "文生图", "llm", "mcp", "openai", "deepseek"]
categories: ["AI"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/2025/app-max-boot-time-on-k8s/"
---

<!--more-->

# 2025年跨平台桌面AI客户端评测报告：普通用户视角

## 1. 引言

随着人工智能技术的飞速发展，AI大模型正以前所未有的速度融入我们的日常生活和工作中。为了让普通用户能够更便捷、高效地利用这些强大的AI能力，各类跨平台桌面AI客户端应运而生。它们旨在提供统一的入口，简化AI模型的使用流程，并集成多种实用功能。

本次评测报告聚焦于七款在2025年备受关注的跨平台桌面AI客户端：**cherry-studio**、**chatbox**、**HyperChat**、**lmstudio**、**deepchat**、**ChatALL**和**gpt4all**。本报告旨在从普通用户的实际需求出发，对这些客户端进行全面、深入的评估，分析它们在功能特性、性能表现、用户体验、模型支持、隐私安全性、扩展性以及社区活跃度等方面的优劣，最终为普通用户提供一份清晰、实用的选型指南。

## 2. 评测方法论

本次评测针对普通用户群体，重点关注客户端的易用性、功能实用性以及稳定性。评测维度及具体考量标准如下：

*   **功能特性 (Functionality):**
    *   **多模型支持与切换便利性：** 支持哪些主流云端模型（如OpenAI, Claude, Gemini, DeepSeek等）和本地模型（通过Ollama, LM Studio等），模型添加和切换是否简便直观。
    *   **对话参数配置：** 是否提供温度（Temperature）、Top-P、最大长度（Max Length）等常见参数的配置选项，配置界面是否易于理解和调整。
    *   **知识库与RAG (Retrieval Augmented Generation)：** 是否支持构建本地知识库，支持哪些文件格式导入，RAG功能是否实用、准确，能否在对话中方便地引用知识库内容。
    *   **MCP (Model Context Protocol) 支持：** 是否支持MCP协议，以及通过MCP提供的工具调用功能对普通用户而言是否易于使用和配置，能否实现文件读写、网页访问等基础自动化任务。
    *   **其他实用功能：** 文件理解（文档、图像、代码）、代码助手、图像生成、Markdown/LaTeX支持、聊天记录管理（搜索、分组、同步）、多窗口/多标签页、语音输入/输出等。
*   **性能 (Performance):**
    *   **响应速度：** 模型推理（尤其是本地模型）和界面响应速度。
    *   **资源消耗：** CPU、内存、GPU占用情况，尤其是在长时间运行或处理复杂任务时。
    *   **稳定性：** 运行过程中是否出现崩溃、卡顿、连接中断等问题。
*   **用户体验 (User Experience):**
    *   **界面设计：** 整体UI是否简洁、直观、美观，是否符合人体工程学设计。
    *   **安装与配置：** 安装过程是否简单（一键安装、无需复杂环境配置），模型和服务配置是否友好（API Key输入、本地模型下载管理）。
    *   **交互流畅度：** 输入是否流畅（无卡顿），对话过程是否顺畅，功能操作是否便捷。
    *   **跨平台支持：** 对Windows、macOS、Linux的支持程度（作为基础评估项），以及对Android、iOS、Web等平台的额外支持（作为加分项）。
    *   **错误提示与帮助文档：** 错误信息是否清晰易懂，是否提供详细的帮助文档或用户指南。
*   **模型支持范围 (Model Support):** 详细列出支持的云端API和本地运行框架/模型格式。
*   **隐私安全性 (Privacy & Security):** 数据（聊天记录、API Key、知识库数据）存储位置和处理方式，是否承诺不收集用户敏感信息，是否支持本地运行以保障隐私。
*   **扩展性 (Extensibility):** 是否支持插件系统，是否允许用户自定义Agent或Prompt，API兼容性如何。
*   **社区活跃度 (Community Activity):** 社区支持渠道（GitHub, Discord, Telegram等），问题响应速度，更新频率。

**综合得分评估方法：**

本次评测采用定性评估与加权评分相结合的方式。每个维度根据上述标准进行详细评估，并赋予相应的权重。针对普通用户，**用户体验**、**功能特性**（特别是多模型支持、知识库、易用参数配置）和**隐私安全性**将获得较高的权重。性能、模型支持范围、扩展性和社区活跃度也占有重要比例。最终综合得分将基于各维度得分乘以权重后汇总得出，并据此进行排名。

## 3. 产品详细评测

本章节将逐一详细评测七款跨平台桌面AI客户端。

### ###### cherry-studio

cherry-studio 被定位为一款**一体化AI智能体**，旨在整合多种LLM应用。它是一款**开源**的跨平台桌面客户端，支持Windows、macOS和Linux，并计划未来支持移动平台（iOS, Android, HarmonyOS）[34][35][44]。

*   **功能特性：** cherry-studio 支持广泛的云服务API，包括OpenAI, Gemini, Anthropic, Claude, Perplexity, Poe等，并通过Ollama和LM Studio支持本地模型[34][36][37][38][43]。它提供超过300个预配置的AI助手，并允许用户创建自定义助手[34][37][42]。其核心功能包括AI驱动的会话命名、Agent和对话的拖放排序、主题切换、完整的Markdown渲染和代码高亮[34][35][41][42]。此外，它集成了AI翻译（专用面板、对话翻译、Prompt翻译）、全局搜索、主题管理系统和迷你程序支持（直接集成Web AI工具）[34][35][37][44][38][39][41]。**知识库管理**是其突出功能，支持导入多种文件格式（文本、图像、Office、PDF）和网页（目录、链接、站点地图）进行向量化和RAG，用户可以在对话中引用知识库生成回复[35][37][44][39][45]。它还提供AI绘画功能[34][37][39]。
*   **性能：** 客户端设计注重效率，模型切换快速[34]。支持Claude-3-7-Sonnet-20250219等模型的流式输出，与某些Web替代品相比速度较快[37][45][50]。
*   **用户体验：** 界面设计**极简且直观**，工作流程高效[34][35][41][42]。被用户评价为“极其出色”和“最全面的本地AI客户端”[34][42]。安装过程简单，“无需环境设置”，对新手友好[39][44][50][52]。配置通常涉及输入API Key[50][52]。
*   **模型支持范围：** 支持OpenAI, Gemini, Anthropic, Claude, Perplexity, Poe, Ollama, LM Studio等，兼容OpenAI API格式的服务商如302ai, cephalon等也得到支持[34][36][37][38][43][48]。
*   **隐私安全性：** 承诺**不收集、存储、传输或处理** API Key、对话数据、知识库数据或任何个人敏感信息[39][46]。仅匿名收集非个人信息用于优化[46]。与LLM的对话数据独立于客户端，客户端仅作为本地接口[39][46]。
*   **扩展性：** **开源**项目（TypeScript, GitHub 28.3k星标），鼓励定制和扩展[34][35][44][38][40][42][47]。支持插件系统（路线图上）和高度可定制的模型参数[35][44][38][45]。
*   **社区活跃度：** 社区活跃，有GitHub Discussions, Telegram, Discord, QQ群, Twitter (X), 小红书, 微博, Bilibili等官方渠道[34][35][44][42][47][48][49]。GitHub显示持续开发活动，近期更新包括重构AI提供商架构、支持新提供商、修复bug等[35][48][49]。
*   **潜在不足：** 尽管功能全面，但作为一体化客户端，某些特定领域的深度可能不如专用工具。插件系统仍在路线图上，当前扩展性主要依赖于其内置功能和API兼容性。

### ###### chatbox

Chatbox 被定位为一款**通用AI客户端**和**桌面AI Copilot**，旨在连接用户与多种领先的AI模型[12][13][74]。

*   **功能特性：** 支持跨平台（Windows, macOS, Linux, 移动和Web）[12][13]。核心功能包括智能文件理解（文档、图像、代码）、代码助手、图像生成、LaTeX和Markdown支持、本地数据存储和跨设备同步[12][13][14]。它连接到多种AI服务，如ChatGPT, Claude等LLMs，并将数据存储在本地（浏览器中）[12][13][74]。提供“Masks”（类似GPTs）用于创建自定义AI工具，支持自动聊天历史压缩和实时响应流式传输[74]。
*   **性能：** 搜索结果中提到存在**输入卡顿**和交互体验有待优化的问题[13][6]。
*   **用户体验：** 界面被评价为**简洁直观**，符合人体工程学设计，支持语音交互，易于使用，被视为提高生产力的工具[24][25][26]。然而，存在**核心缺陷**如输入卡顿、交互体验问题[13][6]。在模型数量多时，缺乏快速搜索、折叠或分组机制，长模型名称可能导致UI显示问题，且无法一键批量添加模型[13][6]。
*   **模型支持范围：** 支持连接到多种AI服务，包括OpenAI, Google AI, Claude等[12][13][74]。与Ollama结合使用被推荐用于AI Agent开发，表明其可以作为本地模型的前端[81]。
*   **隐私安全性：** 承诺本地数据存储（在浏览器中），强调数据隐私[12][13][74]。
*   **扩展性：** 开源版本在GitHub上获得大量星标（15.8K）[14]。支持Masks进行自定义[74]。
*   **社区活跃度：** 开源项目，有一定社区活跃度（GitHub星标数量）[14]。
*   **潜在不足：** 功能相对基础，缺乏RAG或高级多模型管理功能[13][6]。用户体验存在痛点，尤其是在模型管理和输入流畅度方面[13][6]。

### ###### HyperChat

HyperChat，特别是 BigSweetPotatoStudio (`dadigua`) 开发的开源版本，是一款专注于**开放性**的AI聊天客户端，通过**Model Context Protocol (MCP)** 集成各种LLM API和生产力工具[53][54][55][56]。

*   **功能特性：** 支持广泛的兼容OpenAI API格式的LLMs，包括OpenAI (gpt-4o-mini), Claude (通过OpenRouter), Qwen, Deepseek, GLM, Ollama, xAI, Gemini (Gemini Flash 2.0) [53][54][55][56]。核心卖点是**全面支持MCP**， enabling advanced functionalities such as MCP extensions, Tool prompt calls, dynamic modification of Tool parameters, and defining "Agents" with preset prompts and configurable MCP permissions [53][54][55][56]。内置MCP插件市场，简化工具安装配置[53][54]。提供"HyperPrompt"语法，支持变量（文本和JS代码）、基本语法检查和实时预览[53][54]。支持Agent任务调度和状态查看[53][54]。
*   **性能：** 搜索结果中缺乏独立的性能评测和基准测试数据[61]。
*   **用户体验：** 支持暗色模式、中英文界面[53][54]。能渲染Artifacts, SVG, HTML, Mermaid图表和KaTeX数学公式，代码块支持语法高亮和快速复制[53][54]。引入"ChatSpace"概念，支持多聊天实例并行对话[53][54]。然而，**初始设置需要配置API Key和安装系统依赖** (`uv`, `nodejs`)，这对于不熟悉命令行或API管理的普通用户可能构成技术门槛[53][56][74]。
*   **模型支持范围：** 广泛支持兼容OpenAI API格式的云端和本地模型[53][54][55][56]。
*   **隐私安全性：** 与另一个名为"Hyper Chat"的客户端明确声明本地存储数据不同[57][58]，BigSweetPotatoStudio的HyperChat**没有同样清晰、突出的隐私和数据处理声明**，这对于关注隐私的普通用户是一个重要考量点[61]。
*   **扩展性：** **开源**项目（GitHub 606星标），有开发者社区[53][54][55]。全面支持MCP和插件系统，扩展能力强大[53][54][55][56]。
*   **社区活跃度：** 有GitHub社区和Telegram/QQ群支持[53][54][55]。
*   **潜在不足：** 技术门槛较高，不适合完全零基础的普通用户[53][56][74]。缺乏独立的第三方评测和用户反馈，实际使用体验和稳定性有待验证[61]。隐私声明不够明确[61]。需要区分与其他同名产品[57][58][59][60][61][62]。

### ###### lmstudio

LM Studio 是一款面向**初学者和个人用户**的桌面应用，专注于在本地运行大型语言模型，强调**数据隐私和离线操作**[1][2][3][4][5][6]。

*   **功能特性：** 提供**图形用户界面 (GUI)**，极大地简化了本地LLM的运行过程[1][2][3][4][5][6][75][76][77][78][79]。支持直接从Hugging Face下载和管理**GGUF格式**的模型（Llama, Mistral, Phi, Gemma, DeepSeek, Qwen 2.5等）[1][2][3][4][5][6][75]。内置**OpenAI兼容的本地服务器**，可与Open WebUI等前端工具集成[1][2][3][4][6]。提供内置聊天界面和参数调整功能[75]。支持图像生成和嵌入等高级功能[78]。
*   **性能：** 支持NVIDIA/AMD GPU加速（如Apple M系列芯片的MLX框架或CUDA加速），显著降低推理延迟[1][2][4][5][6]。与GPT4All相比，通常需要更高的硬件配置，尤其推荐RTX 2060 8G+显存的GPU，Windows/Linux需要AVX2兼容硬件[1][2][4][6][78]。性能受硬件影响大[19]。
*   **用户体验：** **直观的GUI**是其最大优势，模型下载和运行流程简单，对新手友好[1][2][3][4][5][6][75][76][77][78][79]。内置聊天界面易于使用[75]。
*   **模型支持范围：** 主要支持**GGUF格式**的模型[1][2][4][6]。支持的模型种类广泛，但格式受限[75]。
*   **隐私安全性：** 强调**数据隐私和离线操作**，模型在本地运行，数据不离开用户设备[1][2][3][4][5][6][75][76][77][78][79]。
*   **扩展性：** API功能相对有限（与Ollama等工具相比）[1][2][4][6]。高级任务缺乏深度定制能力[1][2][4][6]。
*   **社区活跃度：** 有一定的用户群体和社区支持[6][78]。
*   **潜在不足：** 模型兼容性仅限于GGUF格式[1][2][4][6]。商业用途需要额外许可，免费版本可能存在性能和模型大小限制[1][2][4][6]。对硬件有一定要求，可能存在“数字鸿沟”[19][1][2][4][6][78]。

### ###### deepchat

DeepChat 是由 ThinkInAIXYZ 开发的一款**独立、开源的跨平台桌面AI助手应用**，与官方DeepSeek客户端不同[63][64][65]。它提供统一界面与多种LLM交互[63].

*   **功能特性：** 支持广泛的兼容OpenAI, Gemini, Anthropic API格式的模型提供商，包括DeepSeek, OpenAI, Silicon Flow, Grok, Gemini, Anthropic, Moonshot, OpenRouter, Azure OpenAI, Qiniu, Zhipu, Hunyuan等[63]。**无缝集成Ollama**，支持在应用内管理、下载、部署和运行本地模型，无需命令行[63]。也支持通过LM Studio运行本地模型[63]。内置**Model Context Protocol (MCP) 支持**，实现代码执行和网页访问等高级工具调用，无需额外配置[63]。支持语义工作流、用户友好配置界面、美观的工具调用显示和详细调试窗口[63]。支持多种搜索引擎增强AI响应，提供可定制的非标准网页搜索[63]。支持**多模态交互**（文本、图像、语音），包括实时语音转文本和文本转语音[63][67][68]。提供完整的Markdown渲染和CodeMirror代码块渲染[63]。支持多窗口和多标签页管理对话[63]。
*   **性能：** 搜索结果中缺乏直接的性能对比数据[73]。
*   **用户体验：** 界面支持亮色和暗色模式[63]。安装方便，提供Windows (.exe), macOS (.dmg), Linux (AppImage, .deb) 可执行文件，macOS也可通过Homebrew安装[63][64]。设计用于多种AI应用场景，作为日常助手、开发辅助、学习工具、内容创作和数据分析工具[63]。
*   **模型支持范围：** 广泛支持兼容OpenAI, Gemini, Anthropic API格式的云端和本地模型，特别是深度集成了Ollama[63]。
*   **隐私安全性：** 强调用户隐私，通过**本地数据存储**和网络代理支持降低信息泄露风险[63]。
*   **扩展性：** **开源**项目（Apache License 2.0），适合商业和个人使用[63]。内置MCP支持提供了强大的扩展潜力[63]。
*   **社区活跃度：** 开源项目，有GitHub社区[63][65][69][71]。
*   **潜在不足：** 需要区分与同名的Web组件项目[66][67][69][70][71][72]。作为相对较新的项目，用户反馈和长期稳定性有待更多验证。

### ###### ChatALL

ChatALL 的核心特点是其**独特的多模型并发对话能力**[15][16][17][18]。

*   **功能特性：** 能够**同时与多个AI聊天机器人**（包括ChatGPT, Gemini AI, DeepSeek, Bing Chat, Bard等）进行并发对话[15][16][17][18]。这使用户能够方便地比较不同模型的回答，尤其适用于解决复杂问题[15][16][17][18]。支持多种语言和操作系统[15][16][17]。允许用户保存聊天历史和高亮偏好回复[15][16][17]。
*   **性能：** 并发请求多个API，性能取决于网络连接和各模型的响应速度。
*   **用户体验：** 界面直观，核心功能突出，即同时显示多个模型的回复[15][16][17][18]。
*   **模型支持范围：** 主要侧重于与**外部或API驱动**的AI服务交互，支持的模型种类广泛，取决于其集成的API列表[15][16][17][18]。**不直接在本地托管和运行大型语言模型**，其本地运行能力体现在客户端应用本身[16][17]。
*   **隐私安全性：** 作为API前端，数据隐私主要取决于用户使用的具体AI服务提供商。客户端本身可能存储聊天历史（本地）[15][16][17]。
*   **扩展性：** **开源**项目[15][16][17][18]。扩展性主要体现在可以集成更多AI服务API。
*   **社区活跃度：** 开源项目，有一定社区活跃度[15][16][17][18]。
*   **潜在不足：** 功能相对单一，主要聚焦于多模型对比，缺乏知识库、高级参数配置、MCP工具调用等功能。不适合需要本地运行模型或深度定制工作流的用户。

### ###### gpt4all

GPT4All 是一个**免费、开源的AI聊天机器人生态系统**，设计用于在**消费级CPU**上本地运行和部署定制化LLMs，**无需互联网连接或独立GPU**（尽管GPU加速可以提升性能）[7][8][9][10][11][19][76][78]。

*   **功能特性：** 提供简洁的用户界面[7][8][10][11]。支持文本到图像生成[7][8][10][11]。无需注册即可使用[7][8][10][11]。支持通过**RAG进行本地文档分析**[78]。提供预配置的模型和对话记忆功能[78]。
*   **性能：** 依赖消费级CPU，可能导致**响应速度较慢且不稳定**[7][8][10][11]。模型文件通常在3GB到8GB之间，需要本地存储空间[7][8][10][11]。对于高级NLP技术和模型训练，需要相当的计算资源[7][8][10][11]。与LM Studio相比，在 modest hardware 上运行良好，但缺乏一些高级功能[78]。
*   **用户体验：** 界面简洁[7][8][10][11]。安装和使用相对简单，适合基本需求用户[78]。
*   **模型支持范围：** 支持数千个模型，但用户普遍认为模型选项有限[19][7][8][10][11]。主要针对可在CPU上运行的模型[7][8][9][10][11]。
*   **隐私安全性：** 极大地保障了用户隐私，数据不被追踪，承诺完全私密的用户体验[7][8][9][10][11][19]。支持完全离线体验[7][8][9][10][11][19]。
*   **扩展性：** 开源项目[7][8][9][10][11]。对高级NLP技术和模型训练存在学习曲线[7][8][10][11]。
*   **社区活跃度：** 开源项目，有一定社区活跃度[7][8][9][10][11]。
*   **潜在不足：** 性能受限于CPU，速度较慢[7][8][10][11]。模型选项相对有限[7][8][10][11]。对于高级用户缺乏深度定制能力[7][8][10][11]。

## 4. 综合对比与分析

本章节将对七款产品在关键评估维度上进行横向对比，重点关注普通用户关注的方面。

| 评测维度                 | cherry-studio                                  | chatbox                                      | HyperChat (BigSweetPotatoStudio)             | lmstudio                                     | deepchat (ThinkInAIXYZ)                      | ChatALL                                      | gpt4all                                      |
| :----------------------- | :--------------------------------------------- | :------------------------------------------- | :------------------------------------------- | :------------------------------------------- | :------------------------------------------- | :------------------------------------------- | :------------------------------------------- |
| **多模型支持与切换**     | 广泛（云+本地），切换便捷                      | 广泛（云），切换存在UI痛点                   | 广泛（云+本地，OpenAI API兼容），切换便捷    | 广泛（本地GGUF），切换便捷                   | 广泛（云+本地，API兼容），切换便捷           | **核心功能**（并发多模型）                   | 有限（本地CPU模型），切换相对简单            |
| **对话参数配置**         | 支持，高度可定制                               | 基础功能                                     | 支持，HyperPrompt强大但有技术门槛            | 支持，内置界面调整                           | 支持                                         | 不支持（依赖后端API）                        | 支持基础参数                                 |
| **知识库与RAG**          | **强大**，支持多种格式导入和对话引用           | **缺乏**                                     | 支持（通过MCP工具）                          | 不支持（需集成其他工具）                     | 支持（通过MCP工具）                          | 不支持                                       | 支持本地文档RAG                              |
| **MCP支持**              | 路线图上（插件系统）                           | 缺乏                                         | **全面支持**，内置插件市场                   | 不支持（需集成其他工具）                     | **内置支持**，工具调用用户友好               | 不支持                                       | 不支持                                       |
| **其他实用功能**         | 文件理解、翻译、搜索、绘画、迷你程序等         | 文件理解、代码助手、图像生成、同步等         | HyperPrompt、Agent、任务调度、富文本渲染等   | 本地服务器、图像生成、嵌入等                 | 多模态、搜索增强、语音交互、多窗口/标签页等  | 并发对话、历史保存、高亮                     | 文本到图像                                   |
| **性能**                 | 高效，支持流式输出，GPU加速（依赖模型）        | 输入卡顿，交互待优化                         | 缺乏独立评测数据                             | GPU加速显著，但硬件要求高，CPU模式较慢       | 缺乏直接评测数据                             | 取决于后端API响应速度                        | CPU依赖，速度较慢，不稳定                    |
| **用户体验**             | 极简直观，安装简单，新手友好                   | 界面友好，但有卡顿和模型管理痛点             | 功能强大但技术门槛高，缺乏独立用户反馈       | GUI直观，模型管理简单，新手友好              | 界面友好，安装方便，功能丰富                 | 核心功能突出，易于比较                       | 界面简洁，安装简单，适合基本需求             |
| **跨平台支持**           | Windows, macOS, Linux (计划移动)               | Windows, macOS, Linux, 移动, Web             | Windows, macOS, Linux (Docker, Web计划中)    | Windows, macOS, Linux                        | Windows, macOS, Linux                        | 多种语言和OS                                 | Windows, macOS, Linux                        |
| **隐私安全性**           | **高**，承诺不收集敏感数据，本地接口           | 本地存储（浏览器），强调隐私                 | 隐私声明不够明确（与同名产品不同）           | **高**，本地运行，数据不离开设备             | **高**，本地数据存储，代理支持               | 取决于后端API，客户端本地存储历史            | **极高**，完全离线，数据不追踪，CPU运行      |
| **扩展性**               | 开源，插件系统（路线图），自定义Agent/Prompt | 开源，Masks自定义                            | 开源，全面MCP支持，插件市场，HyperPrompt     | API功能有限，高级定制不足                    | 开源，内置MCP支持                            | 开源，集成更多API                            | 开源，学习曲线                               |
| **社区活跃度**           | 活跃，多渠道支持，持续更新                     | 开源项目，有一定活跃度                       | 开源项目，有开发者社区                       | 有用户群体和社区                             | 开源项目，有社区                             | 开源项目，有社区                             | 开源项目，有社区                             |
| **技术门槛 (普通用户)**  | 低                                             | 低（但有使用痛点）                           | **高**（需配置API/依赖）                     | 低（GUI友好）                                | 低（安装方便，Ollama集成）                   | 低（核心功能简单）                           | 低（安装简单，CPU运行）                      |

**针对普通用户的深入分析：**

*   **多模型支持与切换便利性：** ChatALL 在并发对比方面独树一帜，适合需要快速比较不同模型回复的用户。cherry-studio 和 deepchat 在支持的模型种类和集成度上表现出色，且切换相对便捷。LM Studio 和 GPT4All 主要侧重本地模型，LM Studio 在本地模型管理GUI方面更胜一筹。Chatbox 支持多种云模型，但模型管理UI有待优化。HyperChat 支持广泛但配置门槛较高。
*   **对话参数配置：** 对于普通用户，参数配置的易用性比可定制性更重要。LM Studio 和 deepchat 提供了易于理解的参数调整界面。cherry-studio 提供高度可定制性，可能更适合有一定探索精神的用户。HyperChat 的HyperPrompt功能强大但需要学习成本。ChatALL 和 GPT4All 的参数配置相对基础。
*   **知识库与RAG：** cherry-studio 在本地知识库构建和RAG功能上表现突出，支持多种文件格式，对需要处理大量本地文档的用户非常实用。GPT4All 也支持本地文档RAG，但功能可能不如cherry-studio全面。其他客户端的RAG功能要么缺乏，要么依赖于MCP工具的集成。
*   **MCP体验：** MCP是连接AI与外部工具的新技术。对于普通用户而言，关键在于工具调用的易用性。DeepChat 内置MCP支持并提供了用户友好的配置和调试界面，降低了使用门槛。HyperChat 全面支持MCP和插件市场，但其整体技术门槛较高。cherry-studio 的插件系统（基于MCP或其他协议）仍在路线图上。
*   **整体用户体验：** LM Studio 和 cherry-studio 在界面直观性和安装简易性方面对新手友好。DeepChat 的安装和Ollama集成也很方便。Chatbox 界面友好但存在输入卡顿等硬伤。GPT4All 界面简洁，适合基本需求。HyperChat 功能强大但设置复杂。ChatALL 的体验围绕其核心并发功能展开。稳定性方面，Claude桌面版曾出现中断和记录丢失问题[20][21]，ChatGPT桌面版也有常见故障[22]，这提示桌面客户端的稳定性是重要考量。输入法兼容性也是潜在问题[33]。
*   **跨平台支持：** 所有七款产品都支持Windows, macOS, Linux，满足基础需求。Chatbox 额外支持移动和Web，cherry-studio 计划支持移动，提供了更广泛的可访问性。
*   **隐私安全性：** LM Studio, GPT4All, deepchat 和 cherry-studio 都强调本地运行或本地数据存储，提供了较高的隐私保障。特别是 GPT4All，其完全离线和CPU运行的特性使其在隐私方面具有独特优势。HyperChat 的隐私声明相对不明确。ChatALL 的隐私取决于后端API。
*   **性能：** 本地模型运行性能是关键差异点。LM Studio 依赖GPU加速以获得更好性能，对硬件有要求。GPT4All 依赖CPU，性能相对较慢但硬件要求低。其他客户端的性能取决于其架构和所连接的API/本地模型。硬件配置是影响本地AI客户端用户体验的“数字鸿沟”[19][27][28][29][30]。
*   **技术门槛：** LM Studio, GPT4All, ChatALL, deepchat 和 cherry-studio 对普通用户相对友好，安装和基础使用门槛较低。HyperChat 由于需要配置API Key和依赖，技术门槛较高。

## 5. 综合得分与排名

基于上述评测维度和对普通用户优先级的考量，我们对七款跨平台桌面AI客户端进行定性评估并赋予得分（满分10分）。请注意，这些得分是基于现有研究信息的**定性评估**，而非严格的性能测试或用户调研数据。

| 排名 | 产品名称      | 综合得分 | 优势概览                                                                 | 劣势概览                                                                 |
| :--- | :------------ | :------- | :----------------------------------------------------------------------- | :----------------------------------------------------------------------- |
| 1    | cherry-studio | 9.0      | 功能全面，知识库/RAG强大，多模型支持广泛，用户体验好，隐私保障高，开源。     | 插件系统仍在路线图上，某些功能深度可能不如专用工具。                       |
| 2    | deepchat      | 8.8      | 多模型支持广泛，无缝Ollama集成，内置MCP支持且用户友好，多模态，隐私保障高。  | 相对较新，长期稳定性待验证，缺乏独立第三方评测。                         |
| 3    | lmstudio      | 8.5      | 本地模型运行GUI友好，模型管理方便，隐私保障高，GPU加速性能好。             | 仅支持GGUF格式，高级定制有限，对硬件有一定要求，商业用途需许可。           |
| 4    | ChatALL       | 8.0      | **独特的多模型并发对比功能**，开源，易于使用。                           | 功能相对单一，不适合本地模型或深度定制需求，隐私取决于后端API。            |
| 5    | gpt4all       | 7.5      | **极高隐私保障**，完全离线，CPU运行硬件要求低，本地RAG支持，开源。         | 性能较慢且不稳定，模型选项相对有限，缺乏高级功能和定制能力。               |
| 6    | chatbox       | 7.0      | 通用AI客户端，多模型支持（云），跨平台广泛，文件理解等功能。               | 用户体验存在输入卡顿和模型管理痛点，缺乏RAG和高级功能。                    |
| 7    | HyperChat     | 6.5      | 全面MCP支持，HyperPrompt强大，多模型兼容性广，开源。                       | **技术门槛高**，不适合普通用户，隐私声明不够明确，缺乏独立评测。           |

**说明：**

*   cherry-studio 和 deepchat 在功能全面性、对普通用户友好的本地/云端模型集成以及对RAG/MCP等新技术的支持方面表现突出，且用户体验和隐私保障较好，因此排名靠前。
*   LM Studio 在本地模型运行的易用性方面是标杆，适合主要需求是本地运行模型的用户。
*   ChatALL 以其独特的多模型并发功能满足了特定用户需求，尽管功能不全面，但在其核心领域表现出色。
*   GPT4All 在隐私和低硬件要求方面有独特优势，适合对隐私要求极高或硬件配置较低的用户。
*   Chatbox 作为通用客户端功能尚可，但用户体验痛点影响了其排名。
*   HyperChat 功能强大且技术前沿（MCP），但较高的技术门槛使其对普通用户不够友好。

## 6. 结论与建议

2025年的跨平台桌面AI客户端市场呈现出多样化的格局，不同产品在功能侧重、技术实现和用户体验上各有千秋。对于普通用户而言，选择最适合自己的客户端需要结合自身的核心需求和技术背景。

**主要发现总结：**

*   **功能集成度提升：** 领先的客户端如 cherry-studio 和 deepchat 不再仅仅是简单的聊天界面，而是集成了多模型支持、知识库/RAG、工具调用（MCP）等多种功能，向“一体化AI工作台”方向发展。
*   **本地模型易用化：** LM Studio 和 deepchat 通过GUI和集成Ollama等方式，显著降低了在本地设备上运行大型语言模型的门槛，使得隐私保护和离线使用成为可能。
*   **多模型并发成为特定需求：** ChatALL 证明了同时比较多个模型回复的需求存在，并提供了专门的解决方案。
*   **用户体验仍有提升空间：** 即使是功能强大的客户端，也可能存在输入卡顿、模型管理不便、错误提示不清晰等用户体验痛点。
*   **隐私和硬件是重要考量：** 本地运行模型提供了强大的隐私保障，但也对用户硬件提出了不同程度的要求，形成了“数字鸿沟”。

**针对普通用户的选型建议：**

*   **如果您追求功能最全面、希望在一个客户端内搞定云端和本地模型、需要强大的知识库/RAG功能，并且注重隐私和用户体验：** **cherry-studio** 或 **deepchat** 是您的首选。两者都提供了丰富的功能和良好的用户体验，且对本地模型的支持友好。deepchat 在内置MCP支持方面可能略有优势，而 cherry-studio 在知识库和整体功能集成度上表现突出。
*   **如果您主要希望在本地运行模型，对GUI友好度和模型管理便利性要求高，且硬件配置尚可：** **lmstudio** 是非常合适的选择。其直观的界面让本地模型运行变得简单。
*   **如果您经常需要比较不同AI模型的回复，以找到最佳答案：** **ChatALL** 是专门为此设计的工具，能够极大地提高您的效率。
*   **如果您对数据隐私有极高要求，希望完全离线运行，或者硬件配置较低（尤其没有高性能GPU）：** **gpt4all** 是一个可靠的选择。它专注于CPU运行和本地隐私，虽然性能可能不如GPU加速的方案。
*   **如果您只需要一个基本的AI聊天客户端，连接到主流云服务，且对高级功能要求不高：** **chatbox** 可以作为入门选择，但需要忍受其在用户体验上的一些不足。
*   **如果您是技术爱好者，希望深入探索MCP协议、自定义Agent和工作流：** **HyperChat** 提供了强大的底层支持和扩展能力，但需要投入学习成本。

**未被充分探索的领域与未来展望（推测）：**

*   **性能基准测试标准化：** 缺乏针对这些桌面客户端在不同硬件和模型下的标准化性能基准测试，这使得普通用户难以准确评估实际运行效果。未来的评测应加强这方面的数据收集。
*   **MCP生态的成熟度：** 虽然MCP协议和支持它的客户端正在兴起，但其插件生态的丰富度和易用性仍需发展。对于普通用户而言，能否方便地发现、安装和使用MCP工具是关键。
*   **跨平台同步与协作：** 随着用户在不同设备上使用AI客户端的需求增加，无缝的跨设备同步和潜在的协作功能将成为重要的竞争点。
*   **更智能的本地RAG：** 知识库功能仍有提升空间，例如更智能的文档解析、更灵活的知识组织方式、以及与AI模型的深度集成，使其能更好地理解和利用本地知识。
*   **用户友好的高级功能：** 如何在提供强大功能（如参数配置、工具调用）的同时，保持界面的简洁和易用性，是所有客户端需要持续优化的方向。例如，提供“简单模式”和“专家模式”等。

总而言之，2025年的跨平台桌面AI客户端市场已经涌现出许多优秀的产品，它们在不同方面满足了用户的需求。通过本报告的详细评测和对比分析，希望能帮助普通用户找到最适合自己的AI助手，更好地利用人工智能的力量。

[1]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFrnVQnwWy5p8HAjsErZOh-Wy4EPcioQ-GwrmvBUUXHmYlT49IMBgpQ4pBu-bX_XFMyXJDws7ZsjuMDQq-AVqwKY7Qezjd2lZBS-oWyKuZWwN9Cx0jHQ43BPEgxJ2R-7S-lISFW5AnttfC0Pc0= "belsterns.com"
[2]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFI7G7eNa3iX0W08FvA_w5UIpcf1Ttcq-P4Efd35_eOMwztH-2PgjlOayewiAxc28qTVH71FbCMXcoCUfbEEjVBg-j9xJaJocu5yKzVaiZcfQ-FAttQ8xYDLy-v1YV9TMnl7wkl "metaschool.so"
[3]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFl0glZWK4axysvd1Ce29EFpT6boh9snHwBhcpx7VY-__bZbqeYeEtkucXN2hf5T4o6BbTYZrpEPNnSwB_D04FdPW2hpbowoowXzFHqsh0bribh3HexNzyOWLWnfM0SafwuVJZpNA7oNfN_HNCX4iVRDUvXPBUkrBa1OmBw24EO8YnM6q8vVs3xSU6aR-HwqQf0FZYCTwfMokj5NcVLE0NwpKc-2m8CIHh8ZXI-4TZ4Bk_GgXgnJKnnJfPEfjsDgk1ntgdLL-bqhbjoUHYOQ3dUMzYQdwtdFyTlPN-T7qI= "toolify.ai"
[4]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFpXvfiEeP7ShSLhqu64lkqVzzeaNn7aN1u5yrNnlLu5WT1_UBYle-LtcSv2-g9PdfrBiO_U5IbOcIv3Z6QeRWlZN8guHdNTuJcmbZ__3iUjoldnbOVKuIsoVbT6Tz3f9YrrB4= "byteplus.com"
[5]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGxtNTCrGFhxhyHpxarMx-b19nHoDt5QWhm9tPVQAekxCiwh5fbhetnhaJHX87mD8Z6OpNxAZYJ698Qj4lZaRyppk6i5dopO6X1Dw_AsGc17JTkxzbGOZzQy6sRl2qmjpl6VPfRi9Ga9KcCd-nG-Q== "openxcell.com"
[6]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQE0A7-YKxdjfYK4HpxEsL83XAQi5lPBpATW9z2iF33UnOn_sj9wgtP8GHMWlwijwiEIxQaVRsVqM-V5okwQJGHPsbrUIpCzTELaHt8wkc3AAzNxG7_ilxRmc45U0W0NoYCkU_wzDUrcmzBoFzpAWw== "csdn.net"
[7]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFZe_C7ACxyNMRk0VkhSOeTFVRJEIUKlXL37QucalM6kC9UzOeQQ4BbAd16zdjHZwr_z9i0BsstRtD4R17TSabmVhbn2yKPbXXHb1jGbqM6sgnGlPO6ratrmNj338jFJT9EX_58Tnh-YZlZbg== "seorocket.ai"
[8]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQG0yG5_x2JpAXYxcVrejmiOB7TPx0DpbeX3R8E9J8N2IK03VcfIxcz0ZU_tR3Sl_VcjcEfbh6lIF3i_AlzfM-TjXA0UikhgOp2Oct3M_ggOlknlLjGVIUGiPRIm-zlEkyj-9HY= "revoyant.com"
[9]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFfCNO6eAoySsBXH9GeMRHTyyp5rVYGaZaL72-JnWjXsBlCe_mNKL3-aOUnRJ3IzIY3n4JLTqfUhbsGVfOiC-YYgIln-m-NqXkv-DE0PueF6ernNL0JhaWadEmTx0ys7iKhs2ur45LfM0DrM1FiWQ== "topai.tools"
[10]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHwG4RxPkFlmelwwca57LRVsPJCNTjR7m7h98vrtCWYaTezOHeauDN-zEgdsjNBwVp4krq7uzy_rPpDc7ZA7Is54gg-vnpQJd65hmuqkMOb_TrbDPVZN0KP9sywCmVMfpVi-M29bw== "vjal.ai"
[11]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHmLRVgXf93yoXPsvdJ1kFiO_htYjjJsk-Y2qk0WzVM5aOSinyHnoaS_k602ssF0qdJp00D2PlmFU6WRB674_KNH1wyR4un0sTffmXhWBF7lL7eKtjwhi5ia_gNYclvq3Ul1IJWq0Wf6ze6R63WqRlKhJQseSSm_eAhxGLBLq5U4mgOo345wFEabLIpbpvJcY6RtjV6Vane4PwhHgD-Yj2QwmSR "toolify.ai"
[12]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFBTFNvP0_rottS7-htUvbqIi0mcQB-bLWjKsBe4zoftrU5M_NuygEeBrX-phtXH-7MXl2-17NjN8rCLHAhGwJEOtzmS8Zo2OpEtgplgXsfBnmBpNfx78LF2e7MRwzX3q2jldVL-QbYgJhSbNcAbeNIPCw5Lm6sYxor8evxE4BS2OOBfA== "apple.com"
[13]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGVUs1ZBQuXHeEeU6eIRcvo0ktIU6e6-s5-UQeH6PGnto8r9gct0TO0_oc3-nIAHoA2kstPx7-G4e5oJLZGxtNcseYYk_7dPD-mNmPqX4a_800i2Y4KJZ3F2fFTu5jSLC7ZYGAQnHz0jbBEk_AjNnfnH_h19StMXeEer2ulul570A9mPbPz "google.com"
[14]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQG2OknZhBXOC0naXtSALQCmkO39znz7yNRSF1uz1tdRKF8VhUXTNvaj1ULbs4XLAusxEv0gIgcCdrzugcNYvPWGDED-D-0kODR7Z89GMj56Z_WyKry9FogS4Pr7CQ2sc-GL3Swrds4uf9gyZO_58oU= "producthunt.com"
[15]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQG4bzbhTCR0eVjlemZVLhHVItCWjpoLYYnF98BLJeHw3uout6RbI4crInMQPH-3Tz12EhYhrjILshBBUKkH5XGPPc-0Vd65MgGQcMO7M7eow8gPstUtMHIAg1tfLwZWlyf-KEWMSZ2Hk2sT63K674g3cJIBou5iARlguHSZWmN3ckw= "apple.com"
[16]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGtKKTSIpKVWSCHL1wxoADZgRXwUl_vchnD12gOntlLQtGdHVvqde7BD7FZvGm45xPewEWdGpBFLeT8VhKZFmEsxjI0MubVmXWnkaRcbYleKdgXB-SnEYAH8eMY0CkSfRmoSaPJgPSEUmNl1-cLv36r_y-zNN1DGCTd7hB39Hb5wgjka0YxYjvt7Y4Q "toolify.ai"
[17]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGdkXrbWOPZGFWJZw5rL_ky6Kp62HBckAOqP8VFv918Vp8PUqJcGCZTXREOkDZ1ZuXotKCvmtis2pkD48VMSLBFe-gKHOG-nGwT6-b4OPG_xFQSYKu5zoWnZdaWL55_o7zARvWXOXePkeunqFhADtqt4K9emCsdDEE17mtlhMPrT3p1 "toolify.ai"
[18]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHBSqOob2h158lWmaSh1py4hew-QHtu_VdZj3Xqkb4gjX2eORxW73kDIL64CIymgeeWbcBG45GDOlHVm2XaDDkb7pXZy5RzJiHUocG-S5tWiGl_N0vaADjnrgFT_oukTIs6BTQF-dE= "youtube.com"
[19]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHOzjAcwZDzzHGsPZDiSPv7k6TqVI2Ak3GTDYr02n1QVScnVplHgtxEWaxMo7Pwsvb_H_jOtU_N7VGRjJn4nk9lI3NFlqyxh-s4dDRr9_IGSpd2tw8ueNvfxpbZ85eR-TYtSkS_aaUPdw== "miracleplus.com"
[20]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGSDcBNguMhobMDxBGHUJ0v2dzlK5NF4brXD29yMmUYwG89tQ72gbR4Y9LGtIIp6n_cGo74WGJXKBps1QPnmtN1ZKLKqORun9bKWHAkj-ta60LXLyuIOmolvqcuBhjdDpSbmuqopQYoJVbBt51GOj7Xxn3_G8UHOg== "feishu.cn"
[21]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQG6oGXVavuoDnvvrw21kGjOGo0y_RxeygLOSG2ZKNVzPQl9J-Hv2SZDxpsjOciEYHAKAsF3RabjiSIjuS_zQGExyr7Qz3t1mEJvfHV1xGSiMuehAFyUrEt7MB1v "yage.ai"
[22]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEY36ETmjTni7IsmUXbXuz5fysY2_VWWKwstp5YhDgLSp8-9rsLQf6iZGUyg1B2l5vYC0WKYWiovPeU9phtsDlGrhIfRNkw34CWIjpToqcKSde0_EZbSDWT6k7LORRPh2SB67-8pGAjY35PkLc= "yuzhouseo.com"
[23]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFBp1UkWtrwxR4dbYwiGo-mBQ0xHezcO9VMS2XXXNTHoeARakfUdKLQi_wyqJttNqmK_TAK7vGzV6HiY-omcvTye7eIPt5ktBpXRvThEVPEJu0URkxdINtsQqR4cntSklOFjwkpOZsjpXAOJV4ikVpZIhw= "csdn.net"
[24]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFr8dantY57tRDo2Km1WVRSgg4Lz4ObQUBVKEmFMb35pFtu-MvcxzjquW74aIPPuZdF7GgbmfBdVYOGoW_pzZcs-k1kIdw5k0exXew4zzE7iOq9K7JpWH1cPTpTONx1ht5nZchdnon9H64MAfaNZzgFb2-CD6GmOQ== "feishu.cn"
[25]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEU711aB0VMcs2R0cJbMj9ABVBvH_AUf_YEWos0fmwbDvJ5HRXyq_EJLAp6yZEUQrzugmred0OkJr_3bg4SB4w8kTOF3mswXauri2Pryn0ol0ElwYyBU0Orl6w8kmCrHEqXhxIrELUhP5SU0lzh2UCsPK2giXyHNolJ1UKUlr8CG0xAtKMtT7SOtT5e30FejssnnU3g_TytWqjV9H4= "toolify.ai"
[26]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEZO1peVlx8hbugIcw2aiUqrC-1DyNfjufCk_iQIfNjQnZ4_wfWZ1JZM-8jCH5C_J1IFTyHofzmNX-qI1ZxT-cliQUq4N_RnqNSk-Z03p1a8JD85SWLdGYLRHyQX4e4gl-llBbHl47ivSB7o9sxwVuxUsL_i64REXk= "csdn.net"
[27]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEb0l8GaETeE1GjZjvTipR-PPG9KhtWliMhYkYkkT5gJIDAnZ7pvrzk74_yLaUbS-APOJpuee0AgBhFPyH2axs4o3Yn2BbU6-cyEo7OKvdPNqXImruuqpmKjDyNWi8IziiQ81ZnjiwQ0g5bCFsLE9r9pgtdfz1jLIACfIQJ5ody1G07YBagWWyB "nvidia.com"
[28]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHFkKTIksYXYQOigLnTrDEiytndDJbr0maKDaQBNeb9VCrJAWvj4kvo-Gk5_tmLPHRb2ZxPMGjJmazxrObaxpJ__py6XNw46adOb7EGtItZIO1317_EAmcjYeGQLmy5zonN7WzPEmqI9N_SyNbKnlH2qcdGvJs= "chrome.com"
[29]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHof985cUTfjwjlS2hKomOmZrqeS3Dxf5RvUSnqRItEGcvTBIdENQz0mKg_Ij3p0cC2jqLRZBrtiQkHscD3uU____bA6G-FzrFUlBbtDGHgDOOCXlWzsFjchZ9fPLGSvQ== "smzdm.com"
[30]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEkFHAiTnz_U5e5VYoD7aR6P88XYSP-mmxdRRigMtvusJA4hiWlLJ5Z1BSQiWHPncCPc0VtB3arN7ukhV51Kmzd5pWgijAwZmFKOCxbzvU-b6pQFY_awmRBHJSrPNHb60NRNO5uasdeEle48WyU0LMqWA== "csdn.net"
[31]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHGqWxV3AmbibNYEXn4qTVv1KpqZe2nHPuK8302kf7HY6RE1pBIKUWgeXtrgArJFYvueHnSEXE8FnbPuTkJdVdZGifgE5UA5JnXhanxSqPDR49kpv6YX4PxmrNojoZmIL55mySjrfknL8JAHyOgi9epBSo8Bufwzcc= "53ai.com"
[32]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHhdIbtm5AaatYn-YcNTOH_Gs76a-uht56nD72rLunceJVuh1ADPF2NLdr41QPHYDn551frHcXnVEagQ4NBwy2Nap4Yeg9jk5Dy2EdVnvGnNTHQBBeoCoF119mgLuiVg-Y2jcsPmlCFi9dTv4s3jjWCrIYi3oHFbkpHXRvmpx3wxDvn6AkmktLyprsGRErVYOaez6xoNrJ7w6VVEMKsdVhW "automationanywhere.com"
[33]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFxKwsqWT8v1SuyFVHYFBnFMJxX4PiMetapQBCGRDnPa-0p4PjFcIlVorxuCzdDFDIp7CkLxo3J7skom6Rh2cYP_wgg2uoY-0bYm9lZyfjLWWnAicRm-CqMSAJaSfRopgdEqintl3Gk-yoC "gptaiflow.tech"
[34]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEgMIfvv_ZDvX4WNrkCq5njfEHgEB4WFVqsiwVHfzmnxDKVtp-kHns044SazovyXSELXQLSXr4qJP8OPT1-oxQIrtr8IRaPO3Z-zmcsbi-JJaBnIMnrfW7TG91O0a8DjeqXIPsFZDD7a7YVSAlA4NVyYX75u97gJ_dRdbfAcVDf2CVgBuGInLOhmq5Uins7ItoI8sTvV5rjdoKc "reddit.com"
[35]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHl-aIPnDUQhcwP-638Y3gpPUy9P6obQhbRiAPnYN9L1VOqlS7G5A3LbDOzv23viw7PHq7i6VOA1MxnyGp5-g2sL0W6-NS08bC4johK4hMWt5kVs-balpRGDNNWAvWaGkb1NMu8 "github.com"
[36]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGyvvdAGnww-4S-GBAYIozF6jBCs4ZpEGgxkfMrENI09GCLOU8br4X-dIcWPY3Y-qkz1H_cOuYlqSDRyIJ32VmZV3xbjeHfoHRZS0516nfuS2dgGBGMPlWh4kvkN9Iyl9U2gYUnAqyTuumc8XGHpcU7OXGXselYRjRz-xaL78NDYtYuOScj "siliconflow.cn"
[37]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQE011q_C9PJ0qzG2wcN9kmYGZQVOuevLky7JEQiqEEm_Xc0KDXl-EJ60Y7u6uNkv1A89jtG1noYqJ_Km0bOJP6B77Y2lN586np6U_K94cuqtZP_rvM1Kpk-EX5yrPtAJUm96Xm0 "toolify.ai"
[38]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEtKmQLTr_6OeEHDAlU2hkFjxlWGTqvHVJIrZdl3QdtE3IdB322ibMX2Kb-C6Q3CckmsjsgEniGC-pio3Xmf5eTQyNbQIHFGw8lfuECWGWxBC1Z16St3CT-FL3cKKFUc_eYNaSb7A== "mcpmarket.com"
[39]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEFZ6vwJt6ECUG0BxEOmZQe3--ua1bubMzWWYqF4WaCnp23TdFZP_51G97mPQ-qhEsLa3khJF0JVqCfAWU6hl6kT82czC2wbUDX3sLx9SG7tRlE2B2nCZHbCj7IIQ== "aibase.com"
[40]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHFJqtgWnuMFsXPFsB9ADb26yq88LB0VcogR6BoWfWiWMahbOsvyDOOzQ8GmFHoRHY-iw60-kG7C-iFW7v_4ZQsfSWwci2NDgi27GKye3s7h6PktkpCOClQ7W3rej6OtE-hsEAvGMmWQh9Au9-LH1eEfnCQSL5b0A== "hellogithub.com"
[41]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGNBDNyCjNzhqTniEAAasxm4-k9hnCmOzJVkbQGvMYwJh8I27Hws3HHFxRl_nxOmvuAVuv-GTLGJ8FzT6zLJtNElUl8By1kO3n5NWsAU5nBC8u_h6wknJRgsS6wvEaS1yz8RC2yxX_vuH2q5yFT "producthunt.com"
[42]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQERWlmPCAS0g08rfO5wkbmCR6EzlSv53oMNMhPeZxMF4ePmsdi9c5KAR3ReJByP-bfmFYy57aa_kIm9kJdJTItsvt7xdDrYMvZHVDVhSVxNQ-TTIBFOs4aOaMpy7mb3oN08A-oOQh4Qod9iOPSv27hTzeE= "alternativeto.net"
[43]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEC8DN40LzCw87yYCMPL_9-teyjVrMvt8KZOD1cbur2XD3MvhqZYaqIYAF8UuG8Gz3-Sd2zoA91kbAAwdIQRVd1CDU9bWES9_vHY8Mhoa6dHrfYSqSpkqdhkfxRKIkz-6AEK-GxSV-cEdEZnQ== "toolify.ai"
[44]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFZG0CpdsXQ1hIbTAYkkZGkchoxL-8oAL6L8oSKpGm1kPMHPsz_NODZGaVzu-jx7IhlqDcGoRlkP9i8P3RaLkdelq-A1eT-ZX0U7EJjP8ZTm75UGcLNO0hc9e8LOio-7QlCe_P-yX0pYwbADABtnxFUpwA= "cherry-ai.com"
[45]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEfuOB1ZGFkfEGMqOKRzntEOw2WBrDXghrODOj8vwSyeG38kxxutr4BffO8DZ_dbrTusgt5VKkY3JME0SPwdsVW40q-lur6FiXQPbxWJ_Cx80qK1utloBNsvCAsHWqcj0sjnxCZGK2h_8y_k6Ak37n4GSTNwMiVwYlQC7OFgLIa5oMEJV6bO3i6IsX9WcZ-6Mjq0NGEfEk8c7UV "reddit.com"
[46]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFrANjBMoa4hF4cw94_h04ZXJ5EyxD2TPVTjpoehLdHNJwlKSYZUii4nqAHgC54Kx9v8-bzgNuY9J7dUpNdv8IKiDD9WR42QhWmHFsUwzaDaAKeODEHhHCWBz4Nnfsq0ffAO8_66LMoctxPitIgsjXK "cherry-ai.com"
[47]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEnX6Jn9OdSLj4fUrwUPXCXURDOu7l4V9gT77vRAc9pApcdYTscKsQ39M8SLFqyUCIKo6iEOAQNcJdYq-Uymqugm30ekQGyfsvLP6-nq9bVDnuU3SXJ4n9_KfLhMubhlp2NF2yzu0uuXizhQjXU "github.com"
[48]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGQ_sjab1g2bynK1nLH4ZHMPsQE3xOG8-8M_MvsRy9espECVfPSOdS86_n45ydI-iQOPeXGppQYW8jbHnwJswgCaSUXC0pMco7ZFM75jEiviPdtTbJ_agLLKSlpj96-u-mcltDtqLxxIFQvLW5PWvrV "github.com"
[49]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQF31c1r2hgS_Iprcdsg_Q2LAqXhPgGicTmON1qPa8MqoUKHzIjAaCyfg98DBQu6_f4-A-3sFGAgz_IhQ_Xg0mQoMplJYvRIhhWcU24rOEoiauQbx2iPlUNMpHZXDm3QkLY= "gitee.com"
[50]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHSA1wodPGL8CJu1W2litfq3H45Ra83ZjWdvAe4r5DewckcJZl2lyl9tWirhqfBAKvZbpRY6GlqoDN-srvBkP44OLo4_sDizQLYamSkC9fJFIFeTtSN-1zU11J2j-yMRb4JcYEuNrsGQD4Av78yS5MtvGGrY2yBuJVShZgmj1i5DEsXPqqu4LAe63MHdb7FPalH "aihubmix.com"
[51]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQE3CoCarnVp24I_JuEZwt6aXlLEkbapRx1b2GBkcf7A0IhKXQXnlGvbr5NoYBMV9yKZh9yaGrz0yBD0kKNWpUoEqq_JCj3p508MQBfWne3OzmoSTalqR-tXyEdud5dkhgVQuE_M8Hc4AY2eVrc= "alternativeto.net"
[52]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHXycNR6IU_rRt1RO-qMgVjcZZLMI-u-pSrwOmtRmqUfLuw2wvUGoLXJujs0XEGpw7pq2lxXwOV9iJYCQxHnrk0zyFdnMSe6jqoxf-IEx6eEwwY2GoYNXmZwbTeUkNZdHvUaOI9svAv "mcp.so"
[53]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHp-QTPwMv3AZQ5UZ3ThDxMlLIFeBuYYC0R1uNHEwlmR_1e6N-a_V6bkeQzDVSjD-7y9rNsrnCbh6itjTA-mrjDRrnjXwdcQ4iMucUktOWLBv2iYR0zoH2NhK99xtWQ0TgICJ-dI8qOEJ7s4jw= "github.com"
[54]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEX6F5emjmNOevQGimTVf2YpPwtnW1jKVHKXgP8WH9-n4Q61M8fyElvkvSGqh77-VTBw4-ezhWV-u14Jn_OjC0FKEhJjIXhNC6T1r27cQv2iGt2qg590ajlDKLwXgk3I_l2t9esZz6-RStH_QE17T7MCuaER7ZdxkpSo2qciJuHxUQ= "github.com"
[55]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQG7N4iDYdomeM9ujOUQ6C8F20OrVpODPGGOqBVWw4Zb2Y7X54DcGDM5YzZLDgldK7_w1nJXo7F2BTihw-XRHTScAFUGeecgEz9t---CH4CfH6EMWm2FtAcMuN-a9El6LKnv98F45B8eCuyKOHtYk1Y= "mcp.so"
[56]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGtCMrBbzbR7s7nSuKvqjsblheHGQRGgz00nIUZZyK3CszM-68anyUZuUEWt0GY2oABwTiZQCIQwDkeMjVIbNtUKgvW8cowUu1fDJoN2Oq_pakmMoHLUyw4ECg= "mcp.so"
[57]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHq9rhLbNDvuLm25z-BL82P-L5poma43oaGxQV8vyw6q61cJeV6jrCB3frNFm8bkDmfJ5Or4zmoXGcpqunbKKMPxGMNqsZnY1XnEwDsrm4bkN_VBbjcLuvQ "yancey.app"
[58]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH5Yh0y6-ySVpE_PZEWU2afwrvRYYX6h6b8U_IxZeZS0CAeli6ZKVymAyBPezYKSYpKwUrFp7Frjz0v1OebgB1A7NqwpNVfWzUHUxTONMrllXaEETLKhvJS5S13I7adAqVyTilb "github.com"
[59]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQE3q35JEjg0WWnkYt5PDaHqZABW2WC56Rp1dCxagHaA15meb2-j9MQVJ0JLm6VFS9U3usNs2Cgwq3B7_Rl8gOu9fCWHMVBN-RK3fmMl-JK3tdsqhthZhS5vvn86n8Hb9q1e1Z7dkyeZdSqF "ai-productreviews.com"
[60]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQExMod_lLE08sS1A2viYxP9y6g9i1jV-e9DowuCtrobnkwmLfl1crE3zebYQBs-o1o8VYyvr0pXVjq2Ods4GPoVvHDmvh40bB1f59l7sbErmeBRbQ79emRE5YfUTj__ZiWhJaQ8tEsF "goldpenguin.org"
[61]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEFhyL-3YBoTu-FhPXN6yTZP0S_-rSNmSAn90tb2qAd8aBLT9Q--0AFa1NRpwVi9JJLVP0XshnnTy2lzFlQFXeSNDlfs-9AGs6KTgo14nLjJxklkr9zWU8z85KZnj30ir8zsWWHsr1QlJv_9AKbI7sTe8nZqqt0wDu5D7pF3lHP4yY= "umairkamil.com"
[62]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEB6GkxUhIG-ROyAPUfD7fTwXY7KB9tn5WY04FZZh6JxXiZMnu42L8cGt3h_6hVR5DnTR5fokTzJrsRl-Wi1U38LfFrJzUAsjvYnhBSQq_7nTVgO9avF6izZ0A0Vp2PN7Lq7tZyLaxmENfou_gH_dbJh0H47kUVH0tz8XVmnZI2hKFycm4= "vargroup.com"
[63]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQF0Qwpo4Q0zqMfM_AgIGaJUUlZKa2Pk8FzAQ1NNlIJibUblo-yrjyOvGgOokIeilJAvLp9bR5C6-g8Iu6qz7ebp5HSLgr07-aFaQ_RMCNqfEYbC1q2qUtun2TBqQEc92c2owGs= "github.com"
[64]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFqyKNprBwW7WrKyXIXP-50kpMxAlhrkTTk6p0eJCD94iQMPD5cumbyXmaJzLkZuRB48baoUH_y4cfKt5w-2RGpxRaJVS5JTZ6PKQveM6vr-83xB2HGotOWYh3kE0Q8CCKf "brew.sh"
[65]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFGo5A94COzBaKIlh-8UzIslRvhzXg4k_jH5wwjSJURRclZJLyD5R7Y6Z9kbukay-PxzW-L6Y7ip53DSLo_iSBabf42uxh0aLZ16GSxHmUfJl7_lSlJpvMkIbWwyLKXQ3d53pf0S3ZrTj5ko8tcAexlUMUSxnym "github.com"
[66]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFenFiyEZ-BVvnflUMg-GuDu9mFwfr8EsG83ZuCcbzMdqlMQ9dTA6oNKTupeM06P_FfFKgxOfo4xp6w5XQaTJX4CE-IU7-O4PtQ2kRRWvZIjg== "deepchat.dev"
[67]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGv--FRpzMtUIDO_7Baw3EY1qWK0uYkFdew3PmnmUxHSw3JuyYaGwM5t3XxHyUl0ZkspYtFYOPvFmgl1jG_JnybEgCBNLF6-gTtV6GKL9HJZ71YV9qClVZR4k3qYK9-vdI_C3eZdKrV_82qqSo9zTUYjG8be0yRJIMq_Ltx8ai9UjGb_rHxjaUFrdRe3-B2Kj3K "promptengineering.org"
[68]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH2-qkfZpl5aForjcCuyNdtLoN7_4PsNGu6NP5prDgV13KBkOtvFGKzHhKXMr4CBZXczDjRu7JapVful8UfIoZC_ktvTY7MpHLaUkXJKYj90rZGbhEJJ_n6YU84Qks_-BRfEjK0 "softonic.com"
[69]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFp9SFHQiZybGwk1Yjx-Pa5f3TEtBAcGOEhxdBJs6yF9VV8t8KYcFlAFAwhiYHw5wP6gYgoiynFXASEKzz_T91Ru5o8I8JScLM6ayYWOuWMMmDpGCsXMF-3u75fuNfDc7y2bUZjDZX8ycg= "github.com"
[70]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEhwtFjJxmAwqiDnDkoAswvFwBrvioapyDYlnCOVMv63erZ8niuAQZGDhZhilrgmj3jGPBVKj2s3__Wr3W2IjA1bgznQJDHq-PNvTkq2NLMbVCwMeSS7uExc9j0uxSUv8wGdA== "deepchat.dev"
[71]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFaPxVC0m_Zyl4vLEOCGxwVb18VBqmQKJy8Uvztd-7_6LZQh7IELglGE28T8GXFg9_lZU7K5ZPhTV5KoBSPANvi8IiEUTEe_kNKMBI2SZVUyfHkjAtzLL9j6BtfyUVgkNfuODH9-sjRAYn9l9IfhV_D6Q== "github.com"
[72]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGuzh8yZ1p4jqLfUobWDBcd4auHt7CcYQE74h-RekFYwGe06FVfJh1x6ZvOYbf4vY_kjTLUELmMDfwW2HHcLv_78krrC59DT7PZ_z7osHU8Mf172YeiApllfxe7NqOHac_zRj4EKgo-sHB6LhJ8yhIi_uvg0fPFvt2lfjokmaIzGAnP9vYVt6lREA== "dev.to"
[73]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQE-fktBP_KiFtooEoGFhgTx7ZSX69rDuA8OBVmRDtrwCGOj9gze3IoYZwICwwGHlYNV1hJLj9ZiecapfooB8x_KZzV-6JvwwsY3ex5xjxjdTtp8_CZ1Kq4xEdfE9pOuiMmSJ9uSZ1bv "zapier.com"
[74]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFwIlC7ZFPI_Ut0ZsjDVjTXSC_aJvsEAe-56npRvgJ7bbprdXkRgeDaVRdzsDSp9e4JtQ35TfPXI25v_UmQFZgdrNNMaHEbvnIHs2Ec5io6USnaUGX9VouYfjGt "wingetgui.com"
[75]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHcG4o4gv-KBeduasDxAjRqVidilNNHQydCizRhFLsOIddTHYkj-s2I99V3wvs885TmLFFjdagou1YsTtnTThim11m8FGIe3D3Lx5CyjNo7FXzSi6bkO2QVdAzjCoIBcUeDNYcaHjjYH71lHPq2xndEiWCaRgSvcZcnT4aiwZq2ygqgwE4bDlo= "dev.to"
[76]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGRirhn0TCc01KLfJy7OslEqCqBSYsBMVLeywh_JoLCzXHvTHhmHr9CGgB3KRr-obXjZQYg_dah49PEKhVtmrZoVQnTjVM-oQ_maknbxw-Yc821PZ__hmlRkaYD4MKT_-H1792Vx4FN8dFvonTvzscpsusyMVo= "unite.ai"
[77]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFulOC1JSrLHYBHtqME0txVeIHo_-SG961ljxI6QPDZaODp2L2rzYlKkYSwXkAQ0vecRHTSo4SuhZmmDd_v-wiOKdUfKPG6vxInAow34SV-djZdT1OHnlrJzfIIBcQRSrHq0OWpt8_Neg== "multitaskai.com"
[78]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH8NGIrNrVXl58ghZQIJQY0gSIxs3fBf3kwfp8NguYUmvTJsIY5OxjftJErN93K0jAh_x-mJUJW_IUO7r54gerfUV8Uxjft45H-83geYXNh-WJ7ggUGKyRgm5iNfy_FWPY50i4VNsn4B1Z41hLusjjUSbS8eCR7wLQWum9r0eS1DDAm2p5uWNExooKFKbA= "ruhanirabin.com"
[79]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHhxmYYGpM2dB1YHZg3OM3HCnJ04PSTaQxoq25V6DMOXGFvxfwoPL4raZqcgPTeTdPI-z3FqXdXqK0oWcqsrFVsRPHh0ZFeJ5AVY26fUbcKXDspJm0p5xJev-AidNMt1Ogl3V41AzQ= "youtube.com"
[80]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEv0gRM0ZiXrkz8p69U6HNBep0EKkREh4WR5xzqmFW0qA29qu8tEsHFUoi8eCpJK_lR63I5HrQDTMx1VQ275uAMF4bWpTWeaPy4bKjLqjjVmPOuBeTcgfrYAUInU4HW1sP9fB1dGxL6b618kn2pJPSjSiSfMosylaI22Ns3BtqhzK_VK0nU3iayctRXQV_QPG_moLaWGesZvEsq5Q== "reddit.com"
[81]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQF7R1sVkgK87s9VPVwz7w0DHs4420S_o0Hwrcw94siXQDNMYyfro_ZGR6-ZitQHh5DNLTp5fFqKOPQyGbSmed8zlOoiq-try20WdJuWjZ-GBYpDWvmYfqAW5ZSXHVu8wmm7-y2CEU7mNiyWIbCOH9VhsgMWFLWDrckJXyV1GQ== "meetup.com"
[82]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQG7lkPgblMumStXvMvGzroT2d6rX9xAM1Yg9NPGqb0rwkvxEKuAsiGHMTzJCnthTl_0w8qU78ALEg8NxcvHetHgIJV40n4Bk63m-CR44oSi42Qx4B4EpzXvNeuZc8pbTpuR7Qp8QD5J_FvTeJeq1mQxAPSYZwA= "kdnuggets.com"
[83]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHu8ithu8shb_oHLBZr-m_fVClv57Gf4QFua4NhOQcfHtg1ySCRm9_qdebGiRvU_6iUFWJmRvagfUcCmyDAG6logi_7ruvyb-6cHf4JYkAHKarciQXAArAko8_YFB-EMeLxkqi1CSYFUfY6TZ-xtMozjU5t82cl8FRWsA== "jhavtech.com.au"
[84]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHVwYXJAgGliPdw9wZPnsVt9RVIgnG4QW1_lSUt6fewlydAuvIt49RjMcL_DVcAzCSv7-QNX4l9A62FqVNYzun_OiebD1y01HUkj73yLGFgrxisD9-jWmGepn63t2UfcouDPXvxByOPoF94Si-u0TMmxydMWXNPIMXkAlrt "shivlab.com"
[85]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGSSK3ph0RM9hmT9-boIC8P8XQm8n4fpY3yY_1hpKfgFpPVDL68S_E0fkCUZnqRzpl6uKvkpXnkN5wGF2B0jpqWV1OXq0rGFZ-Rb1Sgd-q72Ly1qFUsVsERqaqS2NNdFQ4gz8ttu9H3hwqLQXWqULS9ePDRicJMZYQ= "replit.com"
[86]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGdHt428g-KYi5Pvd9p8NTBzNsfiZWMGs1MqYUBPRhKc8uX0iqhy7mFAjkEwkohbKIkVLeVtXRY6LFNozi3ord4O5bWfKjamudjYRDIBneiv6OJ9ovhAQy1rRDX2j03-F1KjMZq9MTjmzWK3flrfpaSP1E= "getzep.com"
[87]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHqOC_9XmjE_15U1pMEzQ5G7j7OMd0Hpq1de03ZwQxHtwzi-UZKcYSdjFRZQ-WpmqMFsasPFWy2dOeQXNnXhJKwCb6rdYKBVms83OfLAh9-CaSUa0kmR3eYGRBdmRJTEPL_ "anthropic.com"
[88]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH1HYuGKcJW4Z51TPx_3VqpyI6u-6J7HKLjx_cq5MKgIInYJCEDt1PlOuqngbZv_HwEocVINYXAAu2GLVxB16e3w_HrWtQbEpppMfRnd28LZ1wtkyB6_729VuvwQcl6e_oSculItZAc9UVQUQ8GrYd7zKzDEp3MiMpIO3A5tPfyGix6e-AbMSRmuCY01mFmmL-ZwOh721nB0o--opPJdhHtdi-mEtjnqUA3uoiL9wWOvjKjT1NlCGDFi0oHO8PlDVTI2fU= "forbes.com"
[89]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHO-lR33wCXuPA9unqv_Fh_EKuG5aJMkoPvPLBIVP0pf5MjyovF4SRudg4rcWzTIsQl_YJDoTOuAN3mlbuA6rSj2gP8Eta2yOn9zjjtcTTUholoZ7NroaWb6jy83avnJEN48j_iwkvWVMYKmoVcA5VUqX3tmHL7mrhYB5xD2-jELEuO7Nm1wRkfBzrqPlTJXhDfqicIHj02TblUKiykng== "reddit.com"
[90]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH60WSpBvgtptDq8grTvr42vGKme1z9RhK-dMlMsPCZz_gSz_nrtfXz_NBfkGtU8Zc9Qf8MpPGBMSg7dC07dO3jIT73XhcDtY1oMTWEpkDYrRhDdgM90ZTfEzJlHlzU0C0-eqhrkgILGxoeVf6q5Ll5RlixIp8= "kdnuggets.com"
[91]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHloJ1aI72XxB6zyNDKJGqzkwOGCzRpIy3U0YghnzkEkYXxmip9vbipsfL69irpAmJS5_CaCxCex5yAOOy8VLqadqAJXKCNtTUWSx3U2sE7xKp-I6zpxFrZHNruhOCLtSakJv5e317MDTnrQMmddZx99VhHIDMe4jlyZ1OK-fVs4ShZ0y-1NyECE6Jfe31sG2I= "mem0.ai"
[92]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQHGpwbokdS64sl1jsQdy_2m-HtHse8mfO0Ah68RwlAWh90kt1Ql0PbgOpzJoPl_NpjKq3Gu3dIlEXD44nw0fbiOkhJmzi9M6okYdfCL78x0R2Tz33vuERpkErvCQPK3j92L98epj4oezuEWsYDnFQwVq6byUZEx1p5Sc-QT "mypurecloud.com"
[93]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFFImfnJ_fQvSZ-HObAE4kYqxblDInnN3E-Am-N6NiwmCZXFeG0bGOn6Rs4qqavMGuOVCuDQR4K_cM5EOB8F750DUj2Aw3fipzFFV9YxrsCdU836wLYCAImK7tnNhJoWShBQyHs22daO9PjAgpREu1Cvfv7vuagZ017GeQnDCBqTqG29oQNuGPR8T25UyVMQVp83lElXSf5rP5O0MgMuoqYPKcT "genesys.com"
[94]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFWKxD27rX2yUcP-IQBIZJnLOXUbT7thtLqVReY8Baa3fdh3Xt01V9Q25VNZukvvTwP1q0aaIEPfUVuR2yfc8JuhzJj74ky3w7lzprK1s2srKukgkzQRgF0AxKNN_lkEFWx80cFYP8UUlECiaTgWRsE-07105dgAHKFj11KffOWyeveeRIj8x_lV_FFdWzxNig93gxF2exsWgRVL7zHSwcUkw62qhBtcimMrpsqt6jjyVp9enCpWt1hz0r4gsC9xnGirOd9Fg== "genesys.com"
[95]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQFG3HXu32bbZGd3A74tUMqrqxxPOdAyOpSqvbHOXo8d2hoL__oYaXtBQ5PqFd6P1ZhlpZ1kLPuWhgEpFgP7myzPLo5vrXbqiatm0F7JOjucV4PqeeZXcZqoT0HPPy8qUGQG8PBhi4-CkY_7mnjVkeN6GKCOZbQcxMwOTk0DsYzD06ZL7G4= "zoom.com"
[96]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQH-BIqeYQbjNE5zL2xLZea4GN8L_jYFL3x6nfr_CCkqRH4QeUJIDIydDDiDKIb-OEpoKS68ONF1cko3B9YDCiSviImlQ86kvhwWe6gqrdnjhmIco07g-wzAT9GDIPaY "teamai.com"
[97]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEAaSVnQDlTg2eYW3ihAlCB58S34DADp67XyjRIhFzDTm1v-kIgtHuxjShzQ5n0kpW3ZU8tpTOzgJshNoXIQ-r7Ne4ojrKRpnBrYcxSoVasigSQ1sTup7JEVhfTVLW9ECe1Mg0DHl34I0omujhI29hFnrY3GF7Tju5_eTwvj4ANAaM9sL3aTfSr2I-eIRiutaSEYPfNObXG_NT331EvJZ6sdwvc "github.com"
[98]: https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQEJvNzMWQrLI6Fi_jY_bKNEkXtmJ_2IQiV5NEwAfQJGnbKWRvDrFXG0x-jyMxwVbHNh4v4Xoc4ZAzsJQRVT3r0b0t_bicDr1EeGXijdwRpFBTLxDObhl23DHWhEuSXrq8ZMWTrbosELyoKHA9CfsyJodT2RuCktxFLvdAWwjzJDF9sO-TaH3qIQOOsvqXVJ "datarobot.com"

---
本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。

![javalover123](https://img.890808.xyz/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)
