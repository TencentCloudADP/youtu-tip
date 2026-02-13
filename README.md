<p align="center"><a href="https://github.com/TencentCloudADP/youtu-tip/releases"><img src="youtu-tip/docs/assets/header.png" alt="Youtu Tip Header"></a></p>

<p align="center">
<a href="README_CN.md"><b>中文</b></a>
| <a href="https://www.youtu-tip.com"><b>Website</b></a>
| <a href="#what-is-tip"><b>Tip Overview</b></a>
| <a href="#how-to-use-tip"><b>Using Tip</b></a>
| <a href="#more-tip-tricks"><b>More Tip tricks</b></a>
| <a href="#youtu-agent"><b>Youtu-Agent</b></a>
| <a href="#youtu-llm-small-and-powerful"><b>Youtu-LLM</b></a>
| <a href="#performance-comparison"><b>Performance</b></a>
</p>

<div align="center">
  <a href="https://youtu.be/c4vczLEmVt4" title="Watch on YouTube">
    <img src="https://img.shields.io/badge/Watch_Demo_on_YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch Demo on YouTube">
  </a>
</div>

Tip is a proactive on-device AI assistant that intelligently understands your current work. As a more user-friendly extension of [Youtu-Agent](https://github.com/TencentCloudADP/Youtu-agent), Tip integrates agent invocation, contextual intent detection and more. It is fully open source, supports offline on-device use, and keeps your privacy secure.

Tip is powered by a series of self-developed lightweight models:
- Youtu-LLM: A compact 1.96B model with powerful native agent capabilities.
  > [🤗 Model](https://huggingface.co/collections/tencent/youtu) | [📑 Technical Report](https://arxiv.org/abs/2512.24618) | [🚀 Quick Start Guide](youtu-llm/README.md)
- Youtu-VL: A multimodal large model based on Youtu-LLM-4B, featuring comprehensive visual perception capabilities.
  > [🤗 Model](https://huggingface.co/collections/tencent/youtu) | [📑 Technical Report](https://arxiv.org/abs/2601.19798) | [🚀 Quick Start Guide](https://github.com/TencentCloudADP/youtu-vl/blob/main/README.md)

You are also free to swap out the model for any alternative you prefer.


---

## What is Tip

### Tip’s core traits

Tip focuses on “better interaction, safer privacy, broader capability”:

- **One hotkey, as the AI super entry**: With minimal interaction, you get the model’s power. Press the hotkey and select text or an image—Tip prepares the context for you. We are building a smarter Spotlight-style entry for a smoother AI experience.
- **On-device models for full privacy**: We support fully offline calls to local model services. All data and processing can run against your own on-device models. The Youtu-LLM series provides strong performance and agent ability for secure local work.
- **Read files, browse pages—no problem**: GUI Agent and Youtu Agent capabilities let Tip simulate mouse/keyboard actions for desktop control, connect to agents/MCP servers/tools for complex tasks, and run a multifunction agent locally.

### Why Tip was built

- **Data and privacy safety**: Many LLM agent apps default to processing data in the cloud. For privacy-sensitive scenarios like social platforms, users may not want screen content sent to cloud models and instead prefer private on-device solutions.
- **The last mile of interaction**: LLM apps usually start with a chat box and require typing. We want a smarter way to complete context: no manual typing, copy/paste, or image uploads—Tip understands what is on screen, completes context, infers intent, and suggests actions to reduce typing and close the interaction gap.
- **On-device agent environment**: Most agents live in the cloud, making it hard to run local tasks like “understand and organize local files” or “check chats on a social platform.” We aim to provide a mature framework and environment so users can run a more capable agent locally.
- **New Desktop Skills, Learn and Master:** We've designed a "GUI skill" mechanism for the GUI Agent, allowing Tip to learn new skills from methods taught to it by users. For example, teaching a large model how to "perform specific data cleanup" or "use user-specific tools to perform tasks," customizing your desktop automation skills.

## How to use Tip

### Installer

We provide a download link: [GitHub Release](https://github.com/TencentCloudADP/youtu-tip/releases)  
> Tip currently supports MacOS devices with Apple Silicon (M-series). More device types are being adapted and packaged quickly.

After downloading, grant the required permissions:
- On first launch, enable screen recording and accessibility permissions so shortcuts and screenshots work correctly.  
  > If Tip is not listed, click the + button, locate Tip, and add it. Permission scope: accessibility is used only to read current selection and simulate keyboard/mouse; screen and audio capture are used only for region screenshots.
- Press `ctrl + shift` to activate Tip and start using it.

<p align="center"><img src="youtu-tip/docs/assets/doc_privacy_en.png" alt="Permissions screenshot" width="720"></p>


### Quick start

In “Settings - Models” you can add models, including on-device offline models (Ollama) or OpenAI SDK-compatible endpoints (local or remote).

Three quick ways to invoke Tip:
- Press `ctrl + shift` to open the chat window and talk directly.
- Select some text, then press `ctrl + shift`; Tip will pick up the selection and continue the dialog with that context.
- Hold `ctrl + shift` to enter screenshot mode: while holding, drag to select a region; release to let Tip read the selected image area and continue the conversation.


## More Tip tricks

### GUI skills

We provide Claude-style “skills”: you can teach the model how to operate the computer and let it remember those actions for future use. For example, teach “find the cheapest flights”: open the site, click “sale flights,” then sort by price.

Add more skills under “Settings - GUI Agent” to help Tip operate the desktop more effectively.


### Youtu Agent

Tip integrates [Youtu Agent](https://github.com/TencentCloudADP/Youtu-agent) to give the model more abilities. In “Settings - Youtu Agent,” switch to a config file. Two demo configs are available: “File manager” (bash/file management) and “File manager plus” (adds some format-parsing ability).

When selecting a file, use “Right click - Open with - Tip” so Tip gets the file path. Click “Agent Execute” to have Tip interpret the file contents.


### Connect on-device models

Our on-device model service supports two entry points:

#### Use the Ollama endpoint

Install and start Ollama, pull, and run a local model:

1. Download: visit ollama.com and click “Download macOS.”
2. Unzip the file, drag `Ollama.app` into Applications, run it, and finish setup (Next -> Install).
3. Open Terminal and run: `ollama serve`
4. Open another Terminal window and run: `ollama pull <model-name>`

Once running, connect Tip:

1. In “Settings - Models,” click Add.
2. In “Channel,” choose “ollama” and enter the model name.
3. Save, then connect it in “Settings - General.”

Youtu-LLM has been adapted to `llama.cpp` and we have submitted a pull request to the `Ollama` project. Support for `ollama` will be available soon. Please stay tuned. Usage of `llama.cpp` installation, please refer to: [README](youtu-llm/README.md#5-llamacpp-deployment).


#### Use the OpenAI endpoint

We also support the standard OpenAI SDK entry. You can use any online provider or local services like `llama-server`.

1. In “Settings - Models,” click Add.
2. In “Channel,” choose “OpenAI SDK” and fill in `base_url`, `api_key`, `model`, etc.
3. Save, then connect it in “Settings - General.”


#### Capability Description

Due to the limited number of parameters, edge models have relatively limited performance. They may not be able to complete some tasks, and the accuracy of their output text may be lower compared to larger models. We provide a simple introductory table to easily distinguish the current capabilities of the edge model:

| Task Name | Specific Example | Edge Model | Large Model |
| --- | --- | :---: | :---: |
| Search Content | “Search xxx on this page” | ✅ | ✅ |
| Simple Visual Location | “Click the xxx button and enter xxx” | ✅ | ✅ |
| Single-Step Logic Task | “Fill out a form” | ❌ | ✅ |
| Multi-Step Reasoning Planning | “Search for flight tickets and compare prices” | ❌ | ✅ |
| Cross-Application Collaboration | “Copy content from application xx to application xx” | ❌ | ✅ |
| Anomaly Self-Correction | “Retry when an error is encountered” | ✅ | ✅ |

If you encounter a problem that the edge model cannot solve, we recommend deploying a model with a larger number of parameters and a trusted access point to improve the user experience.


## Local development

The full source code and architecture are open. You can develop and package locally to customize any feature. See: [README](youtu-tip/README.md)


---


## Youtu-LLM: Small and powerful

We proudly introduce Youtu-LLM: a compact yet powerful LLM with 1.96B parameters, 128K context, and native agent ability. In general evaluations, Youtu-LLM significantly outperforms peers of similar size in commonsense, STEM, coding, and long-context tasks. In agent benchmarks, Youtu-LLM surpasses larger models and completes multiple end-to-end agent tasks.


### Highlights

Youtu-LLM’s main contributions:
- **Designed for STEM capability**: vocabulary, data mix, and multi-stage curriculum center on STEM and agent performance.
- **Native agent ability**: trained with 128K context plus Agentic Mid-training to enable more rounds of interaction on-device.
- **SOTA performance**: based on a dense MLA architecture, Youtu-LLM achieves SOTA results on lightweight LLMs, outperforming traditional dense GQA/MHA. MLA also makes integration into DSV3-oriented ecosystems straightforward.


## Performance comparison

We provide Base and Instruct models with strong results across benchmarks, plus evaluation code to reproduce scores. See [README](youtu-llm/README.md) for details.

### Base Model
#### General Benchmarks
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

#### Agentic Benchmarks
We takes [APTBench](https://github.com/TencentYoutuResearch/APTBench/) for evaluating the agentic capabilities of base model.

| Category | Youtu-LLM-2B-Base | Qwen3-1.7B-Base | SmoLM3-3B-Base | Gemma3-4B-Base | Llama3.1-8B |
| :--- | :---: | :---: | :---: | :---: | :---: |
| Code | **37.9%** | 25.1% | 24.3% | <u>32.8%</u> | 23.6% |
| Deep Research | **38.6%** | 28.5% | 27.2% | <u>36.4%</u> | 30.0% |
| Math | **68.0%** | 59.9% | <u>60.7%</u> | 59.8% | 60.1% |
| Tool | **64.2%** | 56.7% | 59.1% | 61.7% | <u>64.1%</u> |

### Instruct Model
#### General Benchmarks
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

#### Agentic Benchmarks
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


## Using Youtu-LLM

Usage:

```python
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("tencent/Youtu-LLM-2B", trust_remote_code=True)
model = AutoModelForCausalLM.from_pretrained(
    "tencent/Youtu-LLM-2B",
    device_map="auto",
    trust_remote_code=True
)
```

We provide a quick start covering “inference with transformers,” “configure thinking mode,” “tune decoding params,” and “deploy with vLLM and tool use.” See: [README](youtu-llm/README.md)

---

## Youtu-VL: Unleashing Visual Potential via Unified Vision-Language Supervision

**Youtu-VL** is a lightweight yet robust Vision-Language Model (VLM) built on the Youtu-LLM with 4B parameters. It pioneers Vision-Language Unified Autoregressive Supervision (VLUAS), which markedly strengthens visual perception and multimodal understanding. This enables a standard VLM to perform vision-centric tasks without task-specific additions. Across benchmarks, Youtu-VL stands out for its versatility, achieving competitive results on both vision-centric and general multimodal tasks.


### Highlights
Youtu-VL’s main contributions:
- **Vision–Language Unified Autoregressive Supervision (VLUAS)**: Youtu-VL is built on the VLUAS paradigm to mitigate the text-dominant optimization bias in conventional VLMs, where visual signals are treated as passive conditions and fine-grained details are often dropped. Rather than using vision features only as inputs, Youtu-VL expands the text lexicon into a unified multimodal vocabulary through a learned visual codebook, turning visual signals into autoregressive supervision targets. Jointly reconstructing visual tokens and text explicitly preserves dense visual information while strengthening multimodal semantic understanding.
- **Vision-Centric Prediction with a Standard Architecture (no task-specific modules)**: Youtu-VL treats image and text tokens with equivalent autoregressive status, empowering it to perform vision-centric tasks for both dense vision prediction (e.g., segmentation, depth) and text-based prediction (e.g., grounding, detection) within a standard VLM architecture, eliminating the need for task-specific additions. This design yields a versitile general-purpose VLM, allowing a single model to flexibly accommodate a wide range of vision-centric and vsion-language requirements.

## Performance comparison

### Vision-Centric Tasks

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



### General Multimodal Tasks

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


## Using Youtu-VL

Usage:

```python
from transformers import AutoProcessor, AutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained(
    "tencent/Youtu-VL-4B-Instruct", attn_implementation="flash_attention_2", torch_dtype="auto", device_map="cuda", trust_remote_code=True
).eval()
```

We provide a quick start, See: [README](https://github.com/TencentCloudADP/youtu-vl/blob/main/README.md)

## License

Youtu-Tip and Youtu-LLM are open-sourced under the [LICENSE](./LICENSE), while Youtu-VL is open-sourced under the [LICENSE](https://github.com/TencentCloudADP/youtu-vl/blob/main/LICENSE).

## 📚 Citation

If you find this work useful, please consider citing:

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
