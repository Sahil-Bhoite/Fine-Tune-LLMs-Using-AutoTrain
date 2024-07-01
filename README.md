# Easiest Way to Fine-Tune LLMs Using AutoTrain

## Table of Contents
1. [Introduction](#introduction)
2. [Features](#features)
3. [Installation](#installation)
   - [Linux and Mac](#linux-and-mac)
   - [Windows](#windows)
4. [Usage](#usage)
   - [Command Line Interface](#command-line-interface)
   - [AutoTrain UI](#autotrain-ui)
5. [Fine-Tuning Methods](#fine-tuning-methods)
   - [Supervised Fine-Tuning (SFT)](#supervised-fine-tuning-sft)
   - [Odds Ratio Preference Optimization (ORPO)](#odds-ratio-preference-optimization-orpo)
   - [Direct Preference Optimization (DPO)](#direct-preference-optimization-dpo)
   - [Reinforcement Learning from Human Feedback (RLHF)](#reinforcement-learning-from-human-feedback-rlhf)
6. [Dataset Preparation](#dataset-preparation)
7. [Examples](#examples)
8. [Troubleshooting](#troubleshooting)
9. [Contributing](#contributing)
10. [License](#license)
11. [Contact](#contact)
12. [Acknowledgements](#acknowledgements)

## Introduction

AutoTrain revolutionizes the process of fine-tuning large language models (LLMs) by providing an automated, code-minimal approach. This guide offers a comprehensive walkthrough on leveraging AutoTrain to create powerful AI models, covering everything from installation to advanced fine-tuning techniques.

## Features

- Simplified LLM fine-tuning process
- Support for multiple fine-tuning methods (SFT, ORPO, DPO, RLHF)
- User-friendly command-line interface
- Intuitive graphical user interface (AutoTrain UI)
- Seamless integration with Hugging Face Hub
- Compatibility with various LLM architectures

## Installation

### Linux and Mac

1. Create a Conda environment:
   ```
   conda create -n autotrain python=3.11 -y
   ```

2. Activate the environment:
   ```
   conda activate autotrain
   ```

3. Install required packages:
   ```
   pip install autotrain-advanced torch torchvision torchaudio deepspeed flash-attn
   ```

4. Export your Hugging Face token:
   ```
   export HF_TOKEN=your_hugging_face_token
   ```

### Windows

(Include Windows-specific installation instructions if available)

## Usage

### Command Line Interface

#### Training a Model with Supervised Fine-Tuning (SFT)

```bash
autotrain llm \
  --train \
  --model microsoft/Phi-3-mini-4k-instruct \
  --data-path timdettmers/openassistant-guanaco \
  --lr 2e-4 \
  --batch-size 2 \
  --epochs 1 \
  --trainer sft \
  --peft \
  --project-name phi-3-openassistant-guanaco-sft \
  --username YourUsername \
  --push-to-hub \
  --token $HF_TOKEN 
```

#### Training a Model with ORPO

```bash
autotrain llm \
  --train \
  --model microsoft/Phi-3-vision-128k-instruct \
  --data-path Anthropic/hh-rlhf \
  --text-column chosen \
  --rejected-text-column rejected \
  --lr 2e-4 \
  --batch-size 2 \
  --epochs 1 \
  --trainer orpo \
  --chat-template chatml \
  --peft \
  --project-name phi-3-Anthropic/hh-rlhf \
  --username YourUsername \
  --push-to-hub \
  --token $HF_TOKEN 
```

### AutoTrain UI

1. Install additional packages:
   ```
   pip install bitsandbytes
   ```

2. Run the AutoTrain app:
   ```
   autotrain app --host 127.0.0.1 --port 10000
   ```

3. Open your browser and navigate to `http://127.0.0.1:10000`

4. Follow the on-screen instructions to configure and start your training job.

## Fine-Tuning Methods

### Supervised Fine-Tuning (SFT)
SFT involves training the model using input-output pairs. It's ideal for tasks where you have a clear set of desired responses for given inputs.

### Odds Ratio Preference Optimization (ORPO)
ORPO fine-tunes the model based on chosen and rejected responses, optimizing the odds ratio of selecting the preferred response.

### Direct Preference Optimization (DPO)
DPO adjusts model parameters for better discrimination in tasks like classification, focusing on preferred and dispreferred responses.

### Reinforcement Learning from Human Feedback (RLHF)
RLHF incorporates human feedback to refine the model's responses, using a dataset that includes queries, responses, and feedback scores.

## Dataset Preparation

Detailed information on preparing datasets for each fine-tuning method, including CSV and JSON formats, can be found in the `examples/` directory.

## Examples

The `examples/` directory contains sample datasets and scripts demonstrating how to use AutoTrain for various fine-tuning tasks.

## Troubleshooting

(Include common issues and their solutions)

## Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md) for more details.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or further information, please contact:
- Email: work.sahilbhoite@gmail.com
- LinkedIn: [Sahil Bhoite's LinkedIn Profile](https://www.linkedin.com/in/sahilbhoite)

## Acknowledgements

- Hugging Face for their incredible tools and models
- The AutoTrain development team
- All contributors and users of this guide

