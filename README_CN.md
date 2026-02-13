<p align="center"><a href="https://github.com/TencentCloudADP/youtu-tip/releases"><img src="youtu-tip/docs/assets/header_zh.png" alt="Youtu Tip Header Zh"></a></p>

<p align="center">
<a href="README.md"><b>English</b></a>
| <a href="https://www.youtu-tip.com"><b>主页</b></a>
| <a href="#tip-是什么"><b>Tip 简介</b></a>
| <a href="#怎样使用-tip"><b>使用指南</b></a>
| <a href="#tip-的更多技巧"><b>更多技巧</b></a>
| <a href="#youtu-agent"><b>Youtu-Agent</b></a>
| <a href="#youtu-llm-小巧的强大模型"><b>Youtu-LLM</b></a>
| <a href="#性能对比"><b>性能</b></a>
</p>

<div align="center">
  <a href="https://youtu.be/c4vczLEmVt4" title="在 YouTube 上观看">
    <img src="https://img.shields.io/badge/点击查看Demo视频-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="在 YouTube 上观看">
  </a>
</div>

Tip 是一个主动式端侧AI助手，一键调用，智能地理解您当前的工作内容。Tip 是 Youtu-Agent 的一个更易于使用的可视化应用，它集成了桌面自动化、智能体工具、上下文补全等功能。它完全开源，支持离线设备使用，并保障您的隐私安全。

Tip 由自研的一系列轻量级模型驱动：
- Youtu-LLM：1.96B 的小巧大模型，强悍原生智能体能力。
  > [🤗 模型](https://huggingface.co/collections/tencent/youtu) | [📑 技术报告](https://arxiv.org/abs/2512.24618) | [🚀 快速入门](youtu-llm/README_CN.md)
- Youtu-VL: 基于 Youtu-LLM-4B 的多模态大模型，具备全面的视觉感知能力。
  > [🤗 模型](https://huggingface.co/collections/tencent/youtu) | [📑 技术报告](https://arxiv.org/abs/2601.19798) | [🚀 快速入门](https://github.com/TencentCloudADP/youtu-vl/blob/main/README.md)

你也可以随时将模型替换为你喜欢的任何其他模型。


---

## Tip 是什么

### Tip 的核心特点

我们希望 Tip 注重于「更好的交互、更安全的隐私、更全面的功能」：

- **一个按键，就是 AI 的超级入口**：我们希望用户通过最低成本的交互，就能轻松感受大模型的能力。因此，按下热键、选中文本或者图像，Tip 就已经为你准备好相关内容。我们致力于打造更智能的 Spotlight 入口，带来更便捷的智能体验。
- **端侧模型，百分百的隐私**：我们支持完全离线的调用，使用本地的模型服务，所有数据和处理都接入用户本地的大模型服务。我们为端侧提供了 Youtu-llm 系列模型，具有良好的性能表现和 Agent 能力，为理想的工作保驾护航。
- **读文件、看网页，通通在行**：我们提供了 GUI Agent 和 Youtu Agent 两方面能力，不仅能够支持模拟鼠标/键盘来实现桌面操纵，还能接入智能体、MCP 服务器和诸多工具，实现更加复杂的任务，在本地运行一个多功能智能体。
- **桌面新技能，一学就掌握**：我们为 GUI Agent 设计了一种「技能」机制，允许 Tip 从用户教会它的方法来学习新技能。例如，教会大模型如何「执行具体的数据整理」、「使用用户特定工具执行任务」等，定制化属于你的桌面自动化技能。

### Tip 的诞生背景

- **数据与隐私安全**：现有的诸多大模型智能体应用，都默认通过云端服务器处理数据。面对一些隐私场景如社交平台，用户或许不希望屏幕内容被发送到云端大模型，而是希望通过安全、隐私的端侧方案来处理对应的数据。
- **交互的「最后一公里」**：大模型应用的入口普遍是一个聊天框，或者需要用户打字输入需求。我们期待一种更智能的上下文补全方式，用户无需手动打字、复制粘贴、上传图片，而是由应用本身来理解用户目前所处的上下文内容，自动补全上下文、理解意图、提供建议，减少用户的打字成本，解决交互的「最后一公里」。
- **端侧智能体环境**：目前大部分智能体运行的环境都位于云端，例如深度研究等功能，用户难以实际使用智能体来执行本地相关任务，例如让大模型「理解和整理本地文件」，「查一下社交平台的聊天内容」等。我们希望提供一个成熟的框架与环境，支持用户使用更全能的智能体。

## 怎样使用 Tip

### 安装包

我们提供了下载链接，点击下载：[GitHub Release](https://github.com/TencentCloudADP/youtu-tip/releases) 
> Tip 目前仅支持M系列芯片的 MacOS 设备，更多类型设备正在火速适配和打包中

下载后，请打开权限即可使用：
- 首次启动前需要开启屏幕录制、辅助功能等权限，确保快捷键与截图正常工作。
  > 如果列表里面没有显示 Tip，请点击列表左下角的 + 号，找到并添加 Tip。权限声明：申请“辅助功能”权限仅用于获得当前用户选中内容、模拟键盘鼠标操作，申请“录屏与系统录音”权限仅用于屏幕区域截图。
- 按 `ctrl + shift` 激活 Tip，开始使用

<p align="center"><img src="youtu-tip/docs/assets/doc_privacy.png" alt="插图：隐私权限打开" width="360"></p>


### 快速体验

您可以在「设置 - 模型」页面添加模型，包括端侧离线模型（使用 Ollama 服务）、OpenAI SDK 标准接口模型（本地或在线模型）。

快速体验 Tip 的三种调用方式：
- 按下 ctrl + shift 按键，弹出对话窗口，可以直接与 Tip 对话问答；
- 先选中一段文字，然后按下 ctrl + shift 按键，Tip 会感知已经选中的内容，并可以直接基于内容进行继续对话；
- 长按 ctrl + shift 按键，会进入截图模式：保持按键不松开时，可以用鼠标拖拽选择一个区域；放开按键，Tip 就可以感知到已经选中的图像区域，并且可以理解并继续对话。


## Tip 的更多技巧

### GUI skills

我们推出类似于 Claude skills 的使用技巧：可以教会大模型如何操作电脑，并且让它记住和学会相关技能，来在日后更好地实现类似的操作。例如，教会大模型如何「搜索最便宜的机票」：先打开相关网页，然后点击「特价机票」，并且按价格排序。

您可以在「设置 - GUI Agent」页面新增更多使用技巧，帮助 Tip 在操作电脑时更加得心应手。


### Youtu Agent

我们接入了 Youtu Agent，为大模型提供更多能力。您可以在「设置 - Youtu Agent」页面，选择切换到对应的配置文件。目前我们提供了两项 demo 例子，分别是可以执行 bash 命令和文件管理的「File manager」，以及额外包含了部分格式文件解析能力的「File manager plus」配置文件。

您可以在选择文件时，使用「右键 - 打开方式 - Tip」，Tip 就可以直接获得文件的相关路径信息。然后点击「Agent执行」，让 Tip 帮您理解文件内容。


### 接入端侧模型

我们的端侧模型服务支持两种不同的入口：

#### 使用 Ollama 接入点

请按照下面的流程安装并启动 ollama 服务，拉取并且运行本地模型：

1. 下载：访问官网 ollama.com，点击 Download macOS。
2. 解压下载的 zip 文件，将 Ollama.app 拖入“应用程序”文件夹，双击运行并按照提示完成设置（Next -> Install）。
3. 打开终端（Terminal），直接复制并运行以下命令：`ollama serve`
4. 打开另一个终端（可以使用 cmd + N 执行），直接复制并运行以下命令：`ollama pull <模型名称>`

上述命令执行完毕后，就能够在 mac 运行一个 ollama 模型。然后，通过下面的方法接入 Tip：

1. 在「设置 - 模型」页面，点击新增
2. 在「通道」页面选择「ollama」，并且填写模型名字
3. 点击保存，即可在「设置 - 通用」页面点击并接入


#### 使用 OpenAI 接入点

我们也提供了标准的 OpenAI SDK 接入点，可以使用任意在线平台提供的模型服务，也可以使用本地 llama-server 等服务提供的接入点。

1. 在「设置 - 模型」页面，点击新增
2. 在「通道」页面选择「OpenAI SDK」，并且填写 base_url, api_key, model 等相关信息
3. 点击保存，即可在「设置 - 通用」页面点击并接入

我们提供的端侧模型 Youtu-LLM 已经适配 llama.cpp 并已经在 Ollama 项目提交 PR，预计将在近期开放支持，敬请期待。llama.cpp 使用说明详见：[README](youtu-llm/README.md#5-llamacpp-deployment)


#### 能力说明

端侧模型受限于其参数量大小，其表现也相对受限，部分任务可能无法完成，输出文本的准确率相比大型模型也会有所相差。我们提供了一张简单的介绍表格，用于简易区分目前端侧模型的能力边界：

| 任务名称 | 具体例子 | 端侧模型 | 大型模型 |
| --- | --- | --- | --- |
| 搜索内容 | “在该页面搜索xxx” | ✅ | ✅ |
| 简单视觉定位 | “点击xxx按钮、输入xxx” | ✅ | ✅ |
| 单步逻辑任务 | “填写表单” | ❌ | ✅ |
| 多步推理规划 | “查询机票并对比价格” | ❌ | ✅ |
| 跨应用协作 | “从xx应用复制内容到xx应用” | ❌ | ✅ |
| 异常自我修正 | “遇到错误时重试” | ✅ | ✅ |

如遇到端侧模型无法解决的问题，推荐使用更大参数量的模型、可信的接入点进行部署，以提升使用体验。


## 本地开发

我们也提供了完全开源的源代码、架构说明等相关内容，可以直接进行本地开发和打包，自定义您所需要的任何功能。具体详见：[README](youtu-tip/README_CN.md)


---


## Youtu-LLM: 小巧的强大模型

我们隆重推出 Youtu-LLM，这是一个全新、小巧但强大的LLM，仅包含1.96B参数，支持128K上下文，并具备原生智能体能力。在通用评估中，Youtu-LLM在常识、STEM、代码和长文能力上显著优于同等规模的现有LLM；在智能体相关测试中，Youtu-LLM超越了规模更大的领先者，并真正能够完成多个端到端的智能体任务。


### 核心亮点

Youtu-LLM的主要贡献如下:
- **以STEM能力为出发点的设计**：Youtu-LLM的设计以STEM能力和智能体能力为出发点，涉及词表构建、数据配比和多阶段课程学习策略。
- **原生智能体能力**：Youtu-LLM使用128K上下文进行原生训练，并辅以智能体中期训练（Agentic Mid-training），从而能够在端侧场景中实现更多轮次的交互。
- **SOTA 性能**：Youtu-LLM基于dense MLA架构，在轻量级LLM上实现了SOTA性能，超越了传统的dense GQA/MHA范式。MLA 架构也意味着Youtu-LLM可以轻松集成到现有的面向DSV3的生态系统中。


## 性能对比

我们提供了 Base 和 Instruct 两款模型，在大部分基准测试中取得了优异的表现，此外，我们还提供了复现所有分数的评估代码。请查看 [README](youtu-llm/README_CN.md) 来了解更多内容。

### 基础模型
#### 通用基准测试

| Type | Benchmark (Metric) | # Shots | Qwen3-1.7B-Base | SmoLM3-3B-Base | Gemma3-4B-Base | Llama3.1-8B | Youtu-LLM-2B-Base |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Commonsense  | MMLU-Pro (EM) | 5 | 34.9% | 35.3% | 29.4% | <u>36.2%</u> | **48.4%** |
|              | MLQA-Zh (EM) | 3 | 38.1% | 38.0% | 40.3% | <u>43.0%</u> | **43.5%** |
|              | MMLU-ProX-Zh (EM) | 5 | <u>32.5%</u> | 26.7% | 24.2% | 25.4% | **40.7%** |
| STEM         | GSM8K (EM) | 8 | <u>68.2%</u> | 67.3% | 38.5% | 47.8% | **77.6%** |
|              | MGSM-Zh (EM) | 8 | <u>57.1%</u> | 40.7% | 33.0% | 35.9% | **68.9%** |
|              | MATH (EM) | 4 | 28.1% | <u>40.8%</u> | 24.4% | 21.5% | **44.4%** |
|              | BBH (EM) | 3 | 53.0% | 59.8% | 51.6% | **62.9%** | <u>59.8%</u> |
|              | GPQA-MC (Acc. Norm) | 5 | <u>30.4%</u> | 26.6% | 28.6% | 30.1% | **33.3%** |
|              | HLE-MC (Acc. Norm) | 3 | 10.7% | 3.1% | 8.0% | <u>11.5%</u> | **17.4%** |
| Coding       | MBPP (Pass@1) | 3 | <u>55.6%</u> | 51.0% | 45.8% | 49.4% | **66.6%** |
|              | MBPP+ (Pass@1) | 3 | <u>71.0%</u> | 66.1% | 61.9% | 62.7% | **81.8%** |
|              | HumanEval (Pass@1) | 0 | <u>49.9%</u> | 34.8% | 36.6% | 36.0% | **64.6%** |
|              | HumanEval+ (Pass@1) | 0 | <u>41.3%</u> | 28.1% | 28.1% | 28.1% | **57.3%** |
|              | LiveCodeBench v6 (Pass@1) | 3 | <u>5.1%</u> | 2.9% | 2.9% | 3.4% | **9.7%** |
|              | CRUXEval (Pass@1) | 1 | 40.6% | 42.1% | 39.7% | <u>42.3%</u> | **55.9%** |
|              | RepoBench (EM) | 3 | 21.0% | 21.8% | <u>23.0%</u> | **25.2%** | 22.7% |
| Long Context | LongBench v2 (Acc.) | 3 | <u>28.0%</u> | **28.8%** | 26.6% | 27.8% | 27.2% |
|              | NIAH (Acc.) | / | 79.8% | 75.0% | <u>99.5%</u> | **99.8%** | 98.8% |

#### 智能体基准测试
我们使用[APTBench](https://github.com/TencentYoutuResearch/APTBench/)来评估基础模型的智能体能力。

| Category | Qwen3-1.7B-Base | SmoLM3-3B-Base | Gemma3-4B-Base | Llama3.1-8B | Youtu-LLM-2B-Base |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Code | 25.1% | 24.3% | <u>32.8%</u> | 23.6% | **37.9%** |
| Deep Research | 28.5% | 27.2% | <u>36.4%</u> | 30.0% | **38.6%** |
| Math | 59.9% | <u>60.7%</u> | 59.8% | 60.1% | **68.0%** |
| Tool | 56.7% | 59.1% | 61.7% | <u>64.1%</u> | **64.2%** |

### 指令模型
#### 通用基准测试
| Benchmark | DeepSeek-R1-Distill-Qwen-1.5B | Qwen3-1.7B | SmolLM3-3B | DeepSeek-R1-Distill-Llama-8B | Youtu-LLM-2B |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Commonsense Knowledge Reasoning** | | | | | |
| MMLU-Redux | 53.0% | 74.1% | 75.6% | **78.1%** | <u>75.8%</u> |
| MMLU-Pro | 36.5% | 54.9% | 53.0% | <u>57.5%</u> | **61.6%** |
| **Instruction Following & Text Reasoning** | | | | | |
| IFEval | 29.4% | <u>70.4%</u> | 60.4% | 34.6% | **81.2%** |
| DROP | 41.3% | 72.5% | 72.0% | <u>73.1%</u> | **86.7%** |
| MUSR | 43.8% | 56.6% | 54.1% | **59.7%** | <u>57.4%</u> |
| **STEM** | | | | | |
| MATH-500 | 84.8% | 89.8% | <u>91.8%</u> | 90.8% | **93.7%** |
| AIME 24 | 30.2% | 44.2% | 46.7% | <u>52.5%</u> | **65.4%** |
| AIME 25 | 23.1% | <u>37.1%</u> | 34.2% | 34.4% | **49.8%** |
| GPQA-Diamond | 33.6% | 36.9% | 43.8% | <u>45.5%</u> | **48.0%** |
| BBH | 31.0% | 69.1% | 76.3% | **77.8%** | <u>77.5%</u> |
| **Coding** | | | | | |
| HumanEval | 64.0% | 84.8% | 79.9% | <u>88.1%</u> | **95.9%** |
| HumanEval+ | 59.5% | 76.2% | 74.7% | <u>82.5%</u> | **89.0%** |
| MBPP | 51.5% | <u>80.5%</u> | 66.7% | 73.9% | **85.0%** |
| MBPP+ | 44.2% | <u>67.7%</u> | 56.7% | 61.0% | **71.7%** |
| LiveCodeBench v6 | 19.8% | 30.7% | 30.8% | <u>36.8%</u> | **43.7%** |

#### 智能体基准测试
| Benchmark | Qwen3-1.7B | SmolLM3-3B | Youtu-LLM-2B |
| :--- | :---: | :---: | :---: |
| **Deep Research** | | | |
| GAIA | 11.4% | 11.7% | **33.9%** |
| xbench | 11.7% | 13.9% | **19.5%** |
| **Code** | | | |
| SWE-Bench-Verified | 0.6% | 7.2% | **17.7%** |
| EnConda-Bench | 10.8% | 3.5% | **21.5%** |
| **Tool** | | | |
| BFCL V3 | 55.5% | 31.5% | **58.0%** |
| τ²-Bench | 2.6% | 9.7% | **15.0%** |


## 使用 Youtu-LLM

快速使用：

```python
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("tencent/Youtu-LLM-2B", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained(
    "tencent/Youtu-LLM-2B",
    device_map="auto",
    trust_remote_code=True
)
```

更详细的使用内容，包括「基于 transformers 进行推理」、「配置思考模式开关」、「配置解码参数」、「使用 vLLM 部署与工具调用」等具体功能。
详情请参阅： [README](youtu-llm/README_CN.md) 。此外，Youtu-llm 也将在近期提供 Ollama 接入点服务，届时欢迎使用。

---

## Youtu-VL：通过统一的视觉–语言监督释放视觉潜能

Youtu-VL 是一个轻量的视觉–语言模型（Vision-Language Model, VLM），基于 Youtu-LLM（4B 参数规模） 构建。该模型提出了 视觉–语言统一自回归监督（Vision-Language Unified Autoregressive Supervision, VLUAS），显著增强了模型的视觉感知能力与多模态理解能力。这一范式使得标准 VLM 无需引入任何任务特定模块，即可胜任多种以视觉为中心的任务。在多个基准评测中，Youtu-VL 展现出良好的通用性，在视觉中心任务与通用多模态任务上均取得了具有竞争力的性能。


### 亮点
Youtu-VL 的主要贡献包括：

- 视觉–语言统一自回归监督（VLUAS）：Youtu-VL 基于 VLUAS 范式构建，旨在缓解传统 VLM 中普遍存在的“文本主导”优化偏置问题。在该问题中，视觉信号往往仅被作为被动条件输入，细粒度视觉信息容易在训练过程中丢失。不同于仅将视觉特征作为输入，Youtu-VL 通过一个学习得到的视觉码本，将文本词表扩展为统一的多模态词表，使视觉信号本身成为自回归预测的监督目标。通过对视觉 token 与文本的联合重建，模型能够显式保留高密度的视觉信息，同时增强多模态语义理解能力。

- 基于标准架构的视觉中心预测（无需任务特定模块）：Youtu-VL 将图像 token 与文本 token 置于同等的自回归地位，使模型能够在标准 VLM 架构下同时完成视觉中心任务与文本预测任务，包括密集视觉预测（如语义分割、深度估计）以及基于文本的预测任务（如目标定位、目标检测）。该设计避免了对任务特定模块的依赖，构建了一个通用且灵活的 VLM，使单一模型即可适配多种视觉中心及视觉–语言任务需求。

## 性能对比

### 视觉中心任务

| Benchmarks | Youtu-VL 4B (instruct) | Qwen3-VL 4B (instruct) | InternVL-3.5 4B | UFO 8B | GiT 756M | VisionLLM v2 7B | *VLM | *Non-VLM |
|------------|:-------------:|:-------------:|:------------------:|:--------:|:----------:|:------------------:|:------:|:----------:|
| **Visual Grounding** |  |  |  |  |  |  |  |  |
| RefCOCO val | 93.6 | 90.7 | 92.5 | 91.8 | - | 90.0 | 92.6 | 90.5 |
| RefCOCO testA | 95.2 | 92.2 | 94.3 | 94.3 | - | 93.1 | 94.3 | 93.1 |
| RefCOCO testB | 90.8 | 86.7 | 88.2 | 87.5 | - | 87.1 | 91.4 | 88.2 |
| RefCOCO+ val | 90.1 | 82.9 | 87.6 | 86.9 | - | 81.1 | 88.7 | 82.7 |
| RefCOCO+ testA | 93.9 | 89.4 | 92.3 | 91.3 | - | 87.3 | 92.2 | 88.9 |
| RefCOCO+ testB | 85.4 | 75.6 | 81.6 | 80.6 | - | 74.5 | 83.2 | 75.9 |
| RefCOCOg val | 92.2 | 87.3 | 89.6 | 87.9 | - | 85.0 | 89.2 | 86.1 |
| RefCOCOg test | 92.9 | 87.7 | 89.3 | 88.6 | - | 86.4 | 89.3 | 87.0 |
| **Object Detection** |  |  |  |  |  |  |  |  |
| COCO val | 47.1 | - | - | 48.9 | 46.7 | 56.7 | 63.7 | 63.1 |
| **Semantic Segmentation** |  |  |  |  |  |  |  |  |
| ADE20k | 54.2 | × | × | 54.5 | 47.8 | 52.3 | 38.4 | 56.4 |
| Cityscapes | 70.4 | × | × | - | 61.8 | - | 42.0 | 83.3 |
| Context59 | 60.4 | × | × | - | 63.3 | - | 63.6 | 60.8 |
| VOC20 | 92.5 | × | × | - | - | - | 97.1 | - |
| COCOStuff | 52.5 | × | × | 30.2 | 49.1 | - | 39.6 | 45.7 |
| **Referring Segmentation** |  |  |  |  |  |  |  |  |
| RefCOCO val | 80.7 | × | × | 80.0 | × | 76.6 | 80.5 | 79.3 |
| RefCOCO testA | 82.0 | × | × | 81.6 | × | 79.3 | 82.6 | 81.2 |
| RefCOCO testB | 78.4 | × | × | 78.1 | × | 74.3 | 76.9 | 77.8 |
| RefCOCO+ val | 76.2 | × | × | 76.7 | × | 64.5 | 74.3 | 69.5 |
| RefCOCO+ testA | 79.6 | × | × | 79.9 | × | 69.8 | 78.9 | 75.6 |
| RefCOCO+ testB | 71.4 | × | × | 72.3 | × | 61.5 | 68.4 | 63.0 |
| RefCOCOg val | 76.5 | × | × | 75.5 | × | 70.7 | 76.3 | 71.3 |
| RefCOCOg test | 76.6 | × | × | 76.3 | × | 71.2 | 77.0 | 72.0 |
| **Depth Estimation** |  |  |  |  |  |  |  |  |
| NYUv2 | 90.4 | × | × | 93.6 | × | × | 86.8 | 98.8 |
| Cityscapes | 92.7 | × | × | - | × | × | - | 92.1 |
| DDAD | 87.6 | × | × | - | × | × | 74.7 | 88.2 |
| **Human Pose** |  |  |  |  |  |  |  |  |
| MPII | 89.1 | × | × | × | × | - | 89.3 | 93.3 |
| **Image Classification** |  |  |  |  |  |  |  |  |
| ImageNet-ReaL | 89.3 | - | - | × | × | × | 91.1 | 91.2 |
| **Object Counting** |  |  |  |  |  |  |  |  |
| TallyQA-Simple | 85.1 | 79.0 | 77.6 | × | × | × | 84.9 | 86.3 |
| TallyQA-Complex | 74.4 | 64.0 | 66.4 | × | × | × | 72.3 | 77.1 |
| CountBench | 88.6 | 78.4 | 79.4 | × | × | × | 83.1 | 93.8 |



### 通用多模态任务

| Benchmarks | Qwen3-VL 8B (instruct) | InternVL-3.5 4B | Qwen3-VL 4B (instruct) | Youtu-VL 4B (instruct) |
|------------|:--------------------:|:------------------:|:---------------------:|:---------------------:|
| **General VQA** |  |  |  |  |
| MMBench_CN | 84.7 | - | 83.5 | 83.6 |
| MMBench_EN | 84.5 | 80.3 | 83.9 | 83.9 |
| MMStar | 70.9 | 65.0 | 69.8 | 71.1 |
| MME (/2800) | - | 2272 | 2309* | 2384 |
| CVBench_2d | - | - | 79.1* | 80.4 |
| CVBench_3d | - | - | 92.4* | 93.0 |
| ScienceQA_val | - | - | 94.7* | 97.0 |
| SEEDBench_IMG | - | - | 77.0* | 76.9 |
| SEEDBench2 | - | - | 75.9* | 74.5 |
| MMVet | - | - | 68.3* | 64.6 |
| **Multimodal Reasoning & Math** |  |  |  |  |
| VisuLogic | 22.5 | - | 19.0 | 25.7 |
| MMMU_val | 69.6 | 66.6 | 67.4 | 61.1 |
| MMMU-Pro | 55.9 | - | 53.2 | 43.0 |
| CMMMU_val | - | - | 54.6* | 52.6 |
| MathVista_mini | 77.2 | 77.1 | 73.7 | 76.5 |
| MathVerse_mini | 62.1 | 45.8 | 46.8 | 56.5 |
| LogicVista | 55.3 | 41.8 | 53.2 | 52.4 |
| VLMsAreBlind | 74.0 | - | 71.9 | 88.9 |
| **Hallucination** |  |  |  |  |
| HallusionBench | 61.1 | 44.8 | 57.6 | 59.1 |
| CRPE_exist | - | - | 95.6* | 96.9 |
| CRPE_relation | - | 75.0 | 71.0* | 72.2 |
| POPE | - | 88.9 | 89.3* | 86.4 |
| **OCR-related Understanding** |  |  |  |  |
| AI2D_test | 85.7 | 82.6 | 84.1 | 85.6 |
| InfoVQA_val | 83.1 | 78.0 | 80.3 | 79.1 |
| TextVQA_val | - | 77.9 | 80.8* | 79.6 |
| DocVQA_val | 96.1 | 92.4 | 95.3 | 94.4 |
| ChartQA_test | 89.6 | 86.0 | 84.6 | 85.3 |
| OCRBench | 896 | 822 | 881 | 813 |
| SEEDBench2Plus | - | 69.4 | 71.5* | 71.3 |
| CharXivDQ | 83.0 | 71.1 | 76.2 | 79.4 |
| CharXivRQ | 46.4 | 39.6 | 39.7 | 43.8 |
| **Multi-image & Real-world** |  |  |  |  |
| BLINK | 69.1 | 58.1 | 65.8 | 64.3 |
| RealWorldQA | 71.5 | 66.3 | 70.9 | 74.6 |
| MMERealWorld_EN | - | - | 63.0* | 61.5 |
| MMERealWorld_CN | - | 59.8 | 61.3* | 63.5 |
| **GUI Agent** |  |  |  |  |
| ScreenSpot Pro | 54.6 | - | 59.5 | 59.6 |
| OSWorld | 33.9 | - | 26.2 | 38.8 |
| **Text-Centric** |  |  |  |  |
| MMLU-Pro | 71.6 | - | 67.1 | 56.5 |
| MMLU-Redux | 84.9 | - | 81.5 | 76.8 |
| C-Eval | - | 71.9 | 76.5 | 69.1 |
| MuSR | - | - | 46.6 | 58.3 |
| IFEval | 83.7 | - | 82.3 | 76.9 |
| DROP (F1) | - | - | 85.0 | 79.3 |
| BBH | - | - | 84.8 | 71.9 |
| GPQA-Diamond | - | - | 42.9 | 39.8 |


## 使用 Youtu-VL

快速使用：


```python
from transformers import AutoProcessor, AutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained(
    "tencent/Youtu-VL-4B-Instruct", attn_implementation="flash_attention_2", torch_dtype="auto", device_map="cuda", trust_remote_code=True
).eval()
```

更详细的使用内容，请参阅： [README](https://github.com/TencentCloudADP/youtu-vl/blob/main/README.md) 。

## 许可证

Youtu-Tip 项目以及 Youtu-LLM 模型基于 [LICENSE](./LICENSE) 进行开源许可。 Youtu-VL 模型基于 [LICENSE](https://github.com/TencentCloudADP/youtu-vl/blob/main/LICENSE)进行开源许可。


## 引用

如果我们的工作有幸为您带来帮助，还希望您考虑引用这两篇文章:

```bibtex
@article{youtu-agent,
  title={Youtu-Agent: Scaling Agent Productivity with Automated Generation and Hybrid Policy Optimization}, 
  author={Tencent Youtu Lab},
  year={2025},
  eprint={2512.24615},
  archivePrefix={arXiv},
  primaryClass={cs.AI},
  url={https://arxiv.org/abs/2512.24615}, 
}

@article{youtu-llm,
  title={Youtu-LLM: Unlocking the Native Agentic Potential for Lightweight Large Language Models},
  author={Tencent Youtu Lab},
  year={2025},
  eprint={2512.24618},
  archivePrefix={arXiv},
  primaryClass={cs.CL},
  url={https://arxiv.org/abs/2512.24618}, 
}

@article{youtu-vl,
  title={Youtu-VL: Unleashing Visual Potential via Unified Vision-Language Supervision},
  author={Tencent Youtu Lab},
  year={2026},
  eprint={2601.19798},
  archivePrefix={arXiv},
  primaryClass={cs.CV},
  url={https://arxiv.org/abs/2601.19798}, 
}
```
