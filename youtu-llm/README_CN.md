<div align="center">

# <img src="assets/logo.svg" alt="Tencent Youtu Lab Logo" height="26px"> Youtu-LLM: <br>解锁轻量级大语言模型的原生智能体潜力

[🔖 English](README.md) • [🤗 模型](https://huggingface.co/collections/tencent/youtu) • [📑 技术报告](https://arxiv.org/abs/2512.24618) • [⭐ 贡献与创新](#contributions) • [📊 性能对比](#benchmarks) • [🚀 快速入门](#quickstart)

</div>

## 🎯 简介

**Youtu-LLM**是一款全新、小巧但强大的LLM，仅包含1.96B参数，支持128K上下文，并具备原生智能体能力。在通用评估中，Youtu-LLM在常识、STEM、代码和长文能力上显著优于同等规模的现有LLM；在智能体相关测试中，Youtu-LLM超越了规模更大的领先者，并真正能够完成多个端到端的智能体任务。

**Youtu-LLM**具有以下特性：
- 类型: 基于密集[MLA](https://arxiv.org/abs/2405.04434)的自回归LLM
- 发布版本: [Base](https://huggingface.co/tencent/Youtu-LLM-2B-Base)和[Instruct](https://huggingface.co/tencent/Youtu-LLM-2B)
- 总参数量: 1.96B
- 层数: 32
- 注意力头数（MLA）: 16 for Q/K/V
- MLA Rank: 1536 for Q, 512 for K/V 
- MLA维度: 128 for QK Nope, 64 for QK Rope, and 128 for V
- 支持文本长度: 131072
- 词表大小: 128256

<a id="contributions"></a>

## 🚀 贡献与创新

Youtu-LLM的主要贡献如下:
- 🎯 **以STEM能力为出发点的设计**：Youtu-LLM的设计以STEM能力和智能体能力为出发点，涉及词表构建、数据配比和多阶段课程学习策略。
- 💡 **原生智能体能力**：Youtu-LLM使用128K上下文进行原生训练，并辅以智能体中期训练（Agentic Mid-training），从而能够在端侧场景中实现更多轮次的交互。
- ⚡ **SOTA 性能**：Youtu-LLM基于dense MLA架构，在轻量级LLM上实现了SOTA性能，超越了传统的dense GQA/MHA范式。MLA 架构也意味着Youtu-LLM可以轻松集成到现有的面向DSV3的生态系统中。

## 🤗 模型下载
| 模型名称  | 简介 | 下载链接 |
| ----------- | ----------- |-----------
| Youtu-LLM-2B-Base  | Youtu-LLM-2B Base模型 |🤗 [下载链接](https://huggingface.co/tencent/Youtu-LLM-2B-Base)|
| Youtu-LLM-2B | Youtu-LLM-2B Instruct模型 | 🤗 [下载链接](https://huggingface.co/tencent/Youtu-LLM-2B)|
| Youtu-LLM-2B-GGUF | Youtu-LLM-2B Instruct模型，GGUF格式 | 🤗 [下载链接](https://huggingface.co/tencent/Youtu-LLM-2B-GGUF)|

## 📰 最新进展
- [2026.01.28] 现在您可以基于[Transformers>=5.1.0](https://github.com/huggingface/transformers/releases/tag/v5.1.0)直接使用Youtu-LLM-2B.
- [2026.01.07] 现在您可以基于[ModelScope](https://mp.weixin.qq.com/s/JJtQWSYEjnE7GnPkaJ7UNA)微调Youtu-LLM-2B。
- [2026.01.04] 现在您可以基于[LlamaFactory](https://github.com/hiyouga/LlamaFactory/pull/9707)微调Youtu-LLM-2B。

<a id="benchmarks"></a>

## 📊 性能对比

### 基础模型
#### 通用基准测试
| Type | Benchmark (Metric) | # Shots | Youtu-LLM-2B-Base | Qwen3-1.7B-Base | SmoLM3-3B-Base | Gemma3-4B-Base | Llama3.1-8B |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Commonsense | MMLU-Pro (EM) | 5 | **48.4%** | 34.9% | 35.3% | 29.4% | <u>36.2%</u> |
|  | MLQA-Zh (EM) | 3 | **43.5%** | 38.1% | 38.0% | 40.3% | <u>43.0%</u> |
|  | MMLU-ProX-Zh (EM) | 5 | **40.7%** | <u>32.5%</u> | 26.7% | 24.2% | 25.4% |
| STEM | GSM8K (EM) | 8 | **77.6%** | <u>68.2%</u> | 67.3% | 38.5% | 47.8% |
|  | MGSM-Zh (EM) | 8 | **68.9%** | <u>57.1%</u> | 40.7% | 33.0% | 35.9% |
|  | MATH (EM) | 4 | **44.4%** | 28.1% | <u>40.8%</u> | 24.4% | 21.5% |
|  | BBH (EM) | 3 | <u>59.8%</u> | 53.0% | 59.8% | 51.6% | **62.9%** |
|  | GPQA-MC (Acc. Norm) | 5 | **33.3%** | <u>30.4%</u> | 26.6% | 28.6% | 30.1% |
|  | HLE-MC (Acc. Norm) | 3 | **17.4%** | 10.7% | 3.1% | 8.0% | <u>11.5%</u> |
| Coding | MBPP (Pass@1) | 3 | **66.6%** | <u>55.6%</u> | 51.0% | 45.8% | 49.4% |
|  | MBPP+ (Pass@1) | 3 | **81.8%** | <u>71.0%</u> | 66.1% | 61.9% | 62.7% |
|  | HumanEval (Pass@1) | 0 | **64.6%** | <u>49.9%</u> | 34.8% | 36.6% | 36.0% |
|  | HumanEval+ (Pass@1) | 0 | **57.3%** | <u>41.3%</u> | 28.1% | 28.1% | 28.1% |
|  | LiveCodeBench v6 (Pass@1) | 3 | **9.7%** | <u>5.1%</u> | 2.9% | 2.9% | 3.4% |
|  | CRUXEval (Pass@1) | 1 | **55.9%** | 40.6% | 42.1% | 39.7% | <u>42.3%</u> |
|  | RepoBench (EM) | 3 | 22.7% | 21.0% | 21.8% | <u>23.0%</u> | **25.2%** |
| Long Context | LongBench v2 (Acc.) | 3 | 27.2% | <u>28.0%</u> | **28.8%** | 26.6% | 27.8% |
|  | NIAH (Acc.) | / | 98.8% | 79.8% | 75.0% | <u>99.5%</u> | **99.8%** |

#### 智能体基准测试
我们使用[APTBench](https://github.com/TencentYoutuResearch/APTBench/)来评估基础模型的智能体能力。

| Category | Youtu-LLM-2B-Base | Qwen3-1.7B-Base | SmoLM3-3B-Base | Gemma3-4B-Base | Llama3.1-8B |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Code | **37.9%** | 25.1% | 24.3% | <u>32.8%</u> | 23.6% |
| Deep Research | **38.6%** | 28.5% | 27.2% | <u>36.4%</u> | 30.0% |
| Math | **68.0%** | 59.9% | <u>60.7%</u> | 59.8% | 60.1% |
| Tool | **64.2%** | 56.7% | 59.1% | 61.7% | <u>64.1%</u> |


### 指令模型
#### 通用基准测试
| Benchmark | Youtu-LLM-2B | DeepSeek-R1-Distill-Qwen-1.5B | Qwen3-1.7B | SmolLM3-3B | DeepSeek-R1-Distill-Llama-8B |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Commonsense Knowledge Reasoning** |  |  |  |  |  |
| MMLU-Redux | <u>75.8%</u> | 53.0% | 74.1% | 75.6% | **78.1%** |
| MMLU-Pro | **61.6%** | 36.5% | 54.9% | 53.0% | <u>57.5%</u> |
| **Instruction Following & Text Reasoning** |  |  |  |  |  |
| IFEval | **81.2%** | 29.4% | <u>70.4%</u> | 60.4% | 34.6% |
| DROP | **86.7%** | 41.3% | 72.5% | 72.0% | <u>73.1%</u> |
| MUSR | <u>57.4%</u> | 43.8% | 56.6% | 54.1% | **59.7%** |
| **STEM** |  |  |  |  |  |
| MATH-500 | **93.7%** | 84.8% | 89.8% | <u>91.8%</u> | 90.8% |
| AIME 24 | **65.4%** | 30.2% | 44.2% | 46.7% | <u>52.5%</u> |
| AIME 25 | **49.8%** | 23.1% | <u>37.1%</u> | 34.2% | 34.4% |
| GPQA-Diamond | **48.0%** | 33.6% | 36.9% | 43.8% | <u>45.5%</u> |
| BBH | <u>77.5%</u> | 31.0% | 69.1% | 76.3% | **77.8%** |
| **Coding** |  |  |  |  |  |
| HumanEval | **95.9%** | 64.0% | 84.8% | 79.9% | <u>88.1%</u> |
| HumanEval+ | **89.0%** | 59.5% | 76.2% | 74.7% | <u>82.5%</u> |
| MBPP | **85.0%** | 51.5% | <u>80.5%</u> | 66.7% | 73.9% |
| MBPP+ | **71.7%** | 44.2% | <u>67.7%</u> | 56.7% | 61.0% |
| LiveCodeBench v6 | **43.7%** | 19.8% | 30.7% | 30.8% | <u>36.8%</u> |

#### 智能体基准测试
| Benchmark | Youtu-LLM-2B | Qwen3-1.7B | SmolLM3-3B |
| :--- | :---: | :---: | :---: |
| **Deep Research** |  |  |  |
| GAIA | **33.9%** | 11.4% | 11.7% |
| xbench | **19.5%** | 11.7% | 13.9% |
| **Code** |  |  |  |
| SWE-Bench-Verified | **17.7%** | 0.6% | 7.2% |
| EnConda-Bench | **21.5%** | 10.8% | 3.5% |
| **Tool** |  |  |  |
| BFCL V3 | **58.0%** | 55.5% | 31.5% |
| τ²-Bench | **15.0%** | 2.6% | 9.7% |

## 📁 评估复现

我们提供了用于复现上述分数的评估代码。
- 对于[Youtu-LLM-2B-Base](https://huggingface.co/tencent/Youtu-LLM-2B-Base)，所有短文通用基准测试可使用[base_eval](base_eval/)进行评估，智能体指标可使用[APTBench](https://github.com/TencentYoutuResearch/APTBench/)获取。
- 对于[Youtu-LLM-2B](https://huggingface.co/tencent/Youtu-LLM-2B)，所有通用基准测试可使用[instruct_eval](instruct_eval/)进行评估。

<a id="quickstart"></a>

## 🚀 快速入门

本指南将帮助您快速部署并调用 **Youtu-LLM-2B** 模型。该模型支持“思考模式”（Reasoning Mode），能够通过思维链（CoT）生成更高质量的回答。

<details>
<summary>Transformers（>=4.56.0,<=4.57.1）</summary>

如果您想基于较早的transformers版本使用Youtu-LLM-2B，请务必注意从该[commit](https://huggingface.co/tencent/Youtu-LLM-2B/commit/5690998a0a4cae7a7ec970d09262745e00bb6c5c)之前的repo下载模型.

### 1. 环境准备

确保您的 Python 环境已安装 `transformers` 库，且版本符合要求。

```bash
pip install "transformers>=4.56.0,<=4.57.1" torch accelerate

```
> **Note**
> - (1) 当前remote文件适配的transformers版本为：pip install "transformers>=4.56.0,<=4.57.1";
> - (2) 请勿使用transformers==4.57.2，因为该版本存在一个[未修复的重大bug](https://github.com/huggingface/transformers/issues/42395);
> - (3) 如果您想使用更高的transformers版本 (例如4.57.3)，请对modeling_youtu.py做轻量修改，即将"[check_model_inputs](https://huggingface.co/tencent/Youtu-LLM-2B/blob/main/modeling_youtu.py#L474)"改为"check_model_inputs()"。这一修改遵循[patch](https://github.com/huggingface/transformers/commit/ede92a8755e48da7ae1d1b7d976ad581aa5c8327#diff-00deeb775525887b5d4f029e8084dd85737e561d4e2606ec8b4787f55d6cf286).

### 2. 核心代码示例

以下示例展示了如何加载模型、启用思考模式，并利用 `re` 模块解析输出中的“思考过程”与“最终结论”。

```python
import re
from transformers import AutoTokenizer, AutoModelForCausalLM

# 1. Configure Model
model_id = "tencent/Youtu-LLM-2B"

# 2. Initialize Tokenizer and Model
tokenizer = AutoTokenizer.from_pretrained(model_id, trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained(
    model_id,
    device_map="auto",
    trust_remote_code=True
)

# 3. Construct Dialogue Input
prompt = "Hello"
messages = [{"role": "user", "content": prompt}]

# Use apply_chat_template to construct input; set enable_thinking=True to activate Reasoning Mode
input_text = tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True,
    enable_thinking=True
)

model_inputs = tokenizer([input_text], return_tensors="pt").to(model.device)
print("Input prepared. Starting generation...")

# 4. Generate Response
outputs = model.generate(
    **model_inputs,
    max_new_tokens=512,
    do_sample=True,
    temperature=1.0,
    top_k=20,
    top_p=0.95,
    repetition_penalty=1.05
)
print("Generation complete!")

# 5. Parse Results
full_response = tokenizer.decode(outputs[0], skip_special_tokens=True)

def parse_reasoning(text):
    """Extract thought process within <think> tags and the subsequent answer content"""
    thought_pattern = r"<think>(.*?)</think>"
    match = re.search(thought_pattern, text, re.DOTALL)
    
    if match:
        thought = match.group(1).strip()
        answer = text.split("</think>")[-1].strip()
    else:
        thought = "(No explicit thought process generated)"
        answer = text
    return thought, answer

thought, final_answer = parse_reasoning(full_response)

print(f"\n{'='*20} Thought Process {'='*20}\n{thought}")
print(f"\n{'='*20} Final Answer {'='*20}\n{final_answer}")
```
</details>

<details>
<summary>Transformers (>=5.1.0)</summary>

### 1. 环境准备

确保您的 Python 环境已安装 `transformers` 库，且版本符合要求。

```bash
git clone https://github.com/huggingface/transformers.git
cd transformers

# pip
pip install '.[torch]'

# uv
uv pip install '.[torch]'

```

### 2. 核心代码示例

以下示例展示了如何加载模型、启用思考模式，并利用 `re` 模块解析输出中的“思考过程”与“最终结论”。

```python
import re
from transformers import AutoTokenizer, AutoModelForCausalLM

# 1. Configure Model
model_id = "tencent/Youtu-LLM-2B"

# 2. Initialize Tokenizer and Model
tokenizer = AutoTokenizer.from_pretrained(model_id)
model = AutoModelForCausalLM.from_pretrained(
    model_id,
    device_map="auto"
)

# 3. Construct Dialogue Input
prompt = "Hello"
messages = [{"role": "user", "content": prompt}]

# Use apply_chat_template to construct input; set enable_thinking=True to activate Reasoning Mode
input_text = tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True,
    enable_thinking=True
)

model_inputs = tokenizer([input_text], return_tensors="pt").to(model.device)
print("Input prepared. Starting generation...")

# 4. Generate Response
outputs = model.generate(
    **model_inputs,
    max_new_tokens=512,
    do_sample=True,
    temperature=1.0,
    top_k=20,
    top_p=0.95,
    repetition_penalty=1.05
)
print("Generation complete!")

# 5. Parse Results
full_response = tokenizer.decode(outputs[0], skip_special_tokens=True)

def parse_reasoning(text):
    """Extract thought process within <think> tags and the subsequent answer content"""
    thought_pattern = r"<think>(.*?)</think>"
    match = re.search(thought_pattern, text, re.DOTALL)
    
    if match:
        thought = match.group(1).strip()
        answer = text.split("</think>")[-1].strip()
    else:
        thought = "(No explicit thought process generated)"
        answer = text
    return thought, answer

thought, final_answer = parse_reasoning(full_response)

print(f"\n{'='*20} Thought Process {'='*20}\n{thought}")
print(f"\n{'='*20} Final Answer {'='*20}\n{final_answer}")
```
</details>

### 3. 关键配置说明

#### 思考模式开关

在 `apply_chat_template` 方法中，通过 `enable_thinking` 参数控制：

* **True (默认建议)**：激活思维链，适合复杂逻辑推理。
* **False**：直接输出结果，响应速度更快，适合简单对话。

#### 推荐解码参数

根据使用场景，建议调整以下超参数以获得最佳生成效果：

| 参数 | 思考模式 (Reasoning) | 非思考模式 (Normal) |
| --- | --- | --- |
| `do_sample` | `True` | `True` |
| `temperature` | **1.0** (保持创造力) | **0.7** (结果更稳定) |
| `top_p` | 0.95 | 0.8 |
| `top_k` | 20 | 20 |
| `repetition_penalty` | 1.05 | - |

> **提示**：在使用思考模式时，较高的 `temperature` 有助于模型进行更深层的发散性思考。

### 4. vLLM 部署

我们提供使用 **vLLM 0.10.2** 部署模型服务的方法。推荐使用的 Docker 镜像为 `vllm/vllm-openai:v0.10.2`。

#### 集成步骤
首先，执行以下命令将Youtu-LLM模型文件集成到 vLLM 框架中。
*注意：请先解压我们提供的经过调整的[vllm压缩文件](vllm_deploy/modified_vllm.zip)，接着将 `<local_modified_vllm_path>` 替换为刚刚解压的vllm代码路径，将 `<vllm_path>` 替换为 vLLM 的安装路径。*

```bash
cp <local_modified_vllm_path>/0_10_2_official/youtu_llm.py <vllm_path>/vllm/model_executor/models/youtu_llm.py
cp <local_modified_vllm_path>/0_10_2_official/configuration_youtu.py <vllm_path>/vllm/model_executor/models/configuration_youtu.py
cp <local_modified_vllm_path>/0_10_2_official/__init__.py <vllm_path>/vllm/config/__init__.py
cp <local_modified_vllm_path>/0_10_2_official/registry.py <vllm_path>/vllm/model_executor/models/registry.py
```

#### 启动服务
集成完成后，即可使用 vLLM 部署模型，启动命令如下：

```bash
vllm serve <model_path> --trust-remote-code
```

**工具调用 (Tool Call) 支持：**
如果要使用 tool_call 能力，请在启动命令中增加以下参数：

```bash
--enable-auto-tool-choice --tool-call-parser hermes
```

### 5. llama.cpp 部署

对于macOS，可以通过下面的方法安装并使用Youtu-LLM:
```bash
brew install llama.cpp
llama-server -hf tencent/Youtu-LLM-2B-GGUF:Q8_0 --host 0.0.0.0 --port 8081  --log-disable
```

## 📚 Citation

如果本工作对您有帮助，希望您引用我们的文章:

```bibtex
@article{youtu-llm,
  title={Youtu-LLM: Unlocking the Native Agentic Potential for Lightweight Large Language Models},
  author={Tencent Youtu Lab},
  year={2025},
  eprint={2512.24618},
  archivePrefix={arXiv},
  primaryClass={cs.CL},
  url={https://arxiv.org/abs/2512.24618}, 
}
```
