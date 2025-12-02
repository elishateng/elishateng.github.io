---
layout: post
title: LLaMa-Factory Finetune Guide
categories: Blog
description: LLaMa-Factory Finetune Guide
keywords: LLaMa, finetune
---

## LLaMa-Factory Finetune Guide

### 1. Environment Prepare
```
Ubuntu 24.04
NVIDIA GeForce RTX 4090 48G VRAM
128 RAM
2T SSD
```
#### Install miniconda 
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash ~/Miniconda3-latest-Linux-x86_64.sh
```
Reference: https://docs.anaconda.com/miniconda/install/

#### Install depencies
```
conda create -n transformers python=3.9//envname
pip install transformers datasets evaluate peft accelerate gradio optimum sentencepiece
```

### 2. Download model

#### Download LLaMa-Factory:
```
git clone --depth 1 https://github.com/hiyouga/LLaMA-Factory.git
cd LLaMA-Factory
pip install -e ".[torch,metrics]"
```

#### Download Qwen2.5 model:
```
git lfs install
git clone https://huggingface.co/Qwen/Qwen2.5-Coder-7B-Instruct
```

### 3. Prepare dataset

#### Dataset Format
#### Dataset Python Scripts

### 4. Export model and create ollama model
```
llamafactory-cli train config/qwen2.5_coder_7b_lora_sft.yaml //这一步是lora微调
llamafactory-cli webchat config/lora_vllm.yaml // 这一步是测试微调后的模型
llamafactory-cli export config/qwen2.5_coder_7b_lora_sft_merge.yaml  //这一步是导出新模型
sudo ollama create qwen2.5-coder-json2nui -f qwen2.5-coder-7b-figma_json_2_nui/Modelfile //这一步是创建ollama可以使用的模型  
```

### Reference:

Miniconda: https://docs.anaconda.com/miniconda/install/

LLaMA Factory Home Page: https://llamafactory.readthedocs.io/zh-cn/latest/index.html

LLaMa Factory Github: https://github.com/hiyouga/LLaMA-Factory

LLaMA-Factory微调与部署详细流程：从入门到实践 ：https://mp.weixin.qq.com/s/Sv0yZBOjPUrB4eMlZu3Z2g
