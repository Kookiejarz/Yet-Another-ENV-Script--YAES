[中文版](./README.zh.md)

# Yet Another ENV Script

![License](https://img.shields.io/github/license/kookiejarz/runpod_env_script)
![Python](https://img.shields.io/badge/python-3.12-blue)
![CUDA](https://img.shields.io/badge/CUDA-13.0-green)
![uv](https://img.shields.io/badge/package%20manager-uv-purple)
![Platform](https://img.shields.io/badge/platform-Linux-yellow)

A streamlined one-click environment setup script designed for RunPod and other Linux-based AI development environments. It leverages `uv` for high-speed dependency management and integrates Hugging Face high-performance transfer mode.

## 🚀 Quick Start

Run the following command in your terminal (recommended for RunPod PyTorch templates):

```bash
curl -sSL https://raw.githubusercontent.com/kookiejarz/runpod_env_script/main/setup.sh | bash
```

## ✨ Features

- **Ultra-fast installation** — Uses `uv` instead of standard `pip`, dramatically faster dependency resolution and installation.
- **Isolated environments** — Builds two independent virtual environments to prevent dependency conflicts between quantization and inference.
- **High-performance transfer** — Automatically enables `HF_HUB_ENABLE_HF_TRANSFER` and `HF_XET_HIGH_PERFORMANCE` to maximize model download speeds.
- **CUDA optimized** — Configured with PyTorch + CUDA 13.0 index URLs for hardware acceleration out of the box.

## 🛠️ Usage

After the script finishes, two activation scripts are generated in your current directory:

**1. Activate quantization environment**

```bash
source activate_quant.sh
```

Includes: `llmcompressor`, `transformers`, `accelerate`, `datasets`, `pandas`,`torchvision`,`sentencepiece`, `huggingface_hub[cli,hf_transfer]`

**2. Activate inference environment (vLLM)**

```bash
source activate_vllm.sh
```

Includes: `vllm==0.18.0`, `huggingface_hub[cli,hf_transfer]`

**3. Exit environment**

```bash
deactivate
```

## ⚙️ Environment Variables

The activation scripts automatically inject the following configurations:

| Variable | Value | Purpose |
|----------|-------|---------|
| `HF_HUB_ENABLE_HF_TRANSFER` | `1` | Enables the Rust-based Hugging Face transfer accelerator |
| `HF_XET_HIGH_PERFORMANCE` | `1` | Enables high-performance mode for XetHub repositories |

## 📄 License

This project is licensed under the [MIT License](./LICENSE). Copyright (c) 2026 Yunheng Liu.

> **Note:** Please ensure NVIDIA drivers are installed before running. It is recommended to monitor your disk space as AI models and virtual environments can consume significant storage.
