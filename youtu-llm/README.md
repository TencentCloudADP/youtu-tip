<div align="center">

# <img src="assets/logo.svg" alt="Tencent Youtu Lab Logo" height="26px"> Youtu-LLM: <br>Unlocking the Native Agentic Potential for Lightweight Large Language Models

[🔖 中文版](README_CN.md) • [🤗 Models](https://huggingface.co/collections/tencent/youtu) • [📑 Technical Report](https://arxiv.org/abs/2512.24618) • [⭐ Contributions](#contributions) • [📊 Benchmarks](#benchmarks) • [🚀 Getting Started](#quickstart)

</div>

## 🎯 Brief Introduction

**Youtu-LLM** is a new, small, yet powerful LLM, contains only 1.96B parameters, supports 128k long context, and has native agentic talents. On general evaluations, Youtu-LLM significantly outperforms SOTA LLMs of similar size in terms of Commonsense, STEM, Coding and Long Context capabilities; in agent-related testing, Youtu-LLM surpasses larger-sized leaders and is truly capable of completing multiple end2end agent tasks. 

**Youtu-LLM** has the following features:
- Type: Autoregressive Causal Language Models with Dense [MLA](https://arxiv.org/abs/2405.04434)
- Release versions: [Base](https://huggingface.co/tencent/Youtu-LLM-2B-Base) and [Instruct](https://huggingface.co/tencent/Youtu-LLM-2B)
- Number of Parameters: 1.96B
- Number of Layers: 32
- Number of Attention Heads (MLA): 16 for Q/K/V
- MLA Rank: 1,536 for Q, 512 for K/V 
- MLA Dim: 128 for QK Nope, 64 for QK Rope, and 128 for V
- Context Length: 131,072
- Vocabulary Size: 128,256

<a id="contributions"></a>

## 🚀 Contributions and Novelty

The key contributions of Youtu-LLM are as follows:
- 🎯 **STEM-Centric Design**: Youtu-LLM was STEM- and Agentic-centrically designed, encompassing its vocabulary fromation, data mixup and multi-stage curriculum learning.
- 💡 **Native Agentic Talents**: Youtu-LLM was natively trained with 128K long contexts + agentic mid-training, enabling more turns of interaction in on-device scenarios.
- ⚡ **SOTA Performance**: Youtu-LLM achieves SOTA performance on a small LLM based on the dense MLA architecture, surpassing conventional dense GQA/MHA paradigms. The MLA architecture also means that Youtu-LLM can be easily integrated into existing DSV3-oriented ecosystems.

## 🤗 Model Download
| Model Name  | Description | Download |
| ----------- | ----------- |-----------
| Youtu-LLM-2B-Base  | Base model of Youtu-LLM-2B |🤗 [Model](https://huggingface.co/tencent/Youtu-LLM-2B-Base)|
| Youtu-LLM-2B | Instruct model of Youtu-LLM-2B | 🤗 [Model](https://huggingface.co/tencent/Youtu-LLM-2B)|
| Youtu-LLM-2B-GGUF | Instruct model of Youtu-LLM-2B, in GGUF format | 🤗 [Model](https://huggingface.co/tencent/Youtu-LLM-2B-GGUF)|

## 📰 News
- [2026.01.28] You can now directly use Youtu-LLM with [Transformers](https://github.com/huggingface/transformers/pull/43166).
- [2026.01.07] You can now fine-tuning Youtu-LLM with [ModelScope](https://mp.weixin.qq.com/s/JJtQWSYEjnE7GnPkaJ7UNA).
- [2026.01.04] You can now fine-tuning Youtu-LLM with [LlamaFactory](https://github.com/hiyouga/LlamaFactory/pull/9707).

<a id="benchmarks"></a>

## 📊 Performance Comparisons

### Base Model
#### General Benchmarks
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

#### Agentic Benchmarks
We takes [APTBench](https://github.com/TencentYoutuResearch/APTBench/) for evaluating the agentic capabilities of base model.

| Category | Qwen3-1.7B-Base | SmoLM3-3B-Base | Gemma3-4B-Base | Llama3.1-8B | Youtu-LLM-2B-Base |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Code | 25.1% | 24.3% | <u>32.8%</u> | 23.6% | **37.9%** |
| Deep Research | 28.5% | 27.2% | <u>36.4%</u> | 30.0% | **38.6%** |
| Math | 59.9% | <u>60.7%</u> | 59.8% | 60.1% | **68.0%** |
| Tool | 56.7% | 59.1% | 61.7% | <u>64.1%</u> | **64.2%** |

### Instruct Model
#### General Benchmarks
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

#### Agentic Benchmarks
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

## 📁 Reproduce Evaluations

We provide our evaluation codes for reproducing the above scores. 
- For [Youtu-LLM-2B-Base](https://huggingface.co/tencent/Youtu-LLM-2B-Base), all short general benchmarks can be evaluated with [base_eval](base_eval/), and agentic metrics can be obtained with [APTBench](https://github.com/TencentYoutuResearch/APTBench/).
- For [Youtu-LLM-2B](https://huggingface.co/tencent/Youtu-LLM-2B), all benchmarks can be evaluated with [instruct_eval](instruct_eval/).

<a id="quickstart"></a>

## 🚀 Quick Start
This guide will help you quickly deploy and invoke the **Youtu-LLM-2B** model. This model supports "Reasoning Mode", enabling it to generate higher-quality responses through Chain of Thought (CoT).

<details>
<summary>Transformers below 5.0.0.dev0</summary>

If you wish to use Youtu-LLM-2B based on earlier versions of transformers, please make sure to download the model repository before this [commit](https://huggingface.co/tencent/Youtu-LLM-2B/commit/5690998a0a4cae7a7ec970d09262745e00bb6c5c).

### 1. Environment Preparation
Ensure your Python environment has the `transformers` library installed and that the version meets the requirements.

```bash
pip install "transformers>=4.56.0,<=4.57.1" torch accelerate

```
> **Note**
> - (1) We recommend to limit the version of transformers: pip install "transformers>=4.56.0,<=4.57.1", which is comparable with the current remote codes;
> - (2) Do not use transformers==4.57.2, since there is a [bug unfixed](https://github.com/huggingface/transformers/issues/42395);
> - (3) If you would like to maintain a higher version (e.g., 4.57.3), you should slightly modify the "[check_model_inputs](https://huggingface.co/tencent/Youtu-LLM-2B/blob/main/modeling_youtu.py#L474)" in modeling_youtu.py to "check_model_inputs()", following the [patch](https://github.com/huggingface/transformers/commit/ede92a8755e48da7ae1d1b7d976ad581aa5c8327#diff-00deeb775525887b5d4f029e8084dd85737e561d4e2606ec8b4787f55d6cf286).

### 2. Core Code Example

The following example demonstrates how to load the model, enable Reasoning Mode, and use the `re` module to parse the "Thought Process" and the "Final Answer" from the output.

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
<summary>Transformers equals or higher than 5.0.0.dev0</summary>

### 1. Environment Preparation
Ensure your Python environment has the `transformers` library installed and that the version meets the requirements.

```bash
git clone https://github.com/huggingface/transformers.git
cd transformers

# pip
pip install '.[torch]'

# uv
uv pip install '.[torch]'

```

### 2. Core Code Example

The following example demonstrates how to load the model, enable Reasoning Mode, and use the `re` module to parse the "Thought Process" and the "Final Answer" from the output.

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

### 3. Key Configuration Details

#### Reasoning Mode Toggle

Controlled via the `enable_thinking` parameter in the `apply_chat_template` method:

* **True (Recommended Default):** Activates Chain of Thought; ideal for complex logic and reasoning tasks.
* **False:** Outputs results directly; faster response time, suitable for simple conversations.

#### Recommended Decoding Parameters

Depending on your use case, we suggest adjusting the following hyperparameters for optimal generation:

| Parameter | Reasoning Mode | Normal Mode |
| --- | --- | --- |
| `do_sample` | `True` | `True` |
| `temperature` | **1.0** (Maintains creativity) | **0.7** (More stable results) |
| `top_p` | 0.95 | 0.8 |
| `top_k` | 20 | 20 |
| `repetition_penalty` | 1.05 | - |

> **Tip:** When using Reasoning Mode, a higher `temperature` helps the model perform deeper, more divergent thinking.

### 4. vLLM Deployment

We provide support for deploying the model using **vLLM 0.10.2**. The recommended Docker image is `vllm/vllm-openai:v0.10.2`.

#### Integration Steps
First, execute the following commands to integrate the Youtu-LLM model files into the vLLM framework.
*Note: Please extract our provided [modified vllm zip file](vllm_deploy/modified_vllm.zip) first. Then, replace `<local_modified_vllm_path>` with the path to the extracted vllm directory, and replace `<vllm_path>` with the installation path of vLLM.*

```bash
cp <local_modified_vllm_path>/0_10_2_official/youtu_llm.py <vllm_path>/vllm/model_executor/models/youtu_llm.py
cp <local_modified_vllm_path>/0_10_2_official/configuration_youtu.py <vllm_path>/vllm/model_executor/models/configuration_youtu.py
cp <local_modified_vllm_path>/0_10_2_official/__init__.py <vllm_path>/vllm/config/__init__.py
cp <local_modified_vllm_path>/0_10_2_official/registry.py <vllm_path>/vllm/model_executor/models/registry.py
```

#### Service Startup
Once integrated, you can deploy the model using the following command:

```bash
vllm serve <model_path> --trust-remote-code
```

**Tool Call Support:**
To enable tool calling capabilities, please append the following arguments to the startup command:

```bash
--enable-auto-tool-choice --tool-call-parser hermes
```

### 5. llama.cpp Deployment

For macOS, you can install and use Youtu-LLM as follows:
```bash
brew install llama.cpp
llama-server -hf tencent/Youtu-LLM-2B-GGUF:Q8_0 --host 0.0.0.0 --port 8081  --log-disable
```

## 📚 Citation

If you find this work useful, please consider citing:

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
