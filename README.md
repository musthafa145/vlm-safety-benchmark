# VLM Safety Benchmark

## Overview

This repository contains experimental work on using a Vision-Language Model (VLM) to identify personal protective equipment (PPE) compliance in CCTV-style video.

The experiment uses **Qwen2.5-VL-3B-Instruct** with a LoRA fine-tuning approach. The goal is to explore whether a vision-language model can identify workers and report visible PPE violations, such as missing helmets.

## Repository Structure

```text
vlm-safety-benchmark/
├── notebooks/
│   ├── qwen_vl_ppe_finetuning_kaggle.ipynb
│   └── qwen_vl_ppe_inference_colab.ipynb
└── README.md
```

The notebooks are maintained in separate Git branches:

- `finetuning-notebook` — fine-tuning experiment performed in Kaggle.
- `inference-attempt` — inference and video evaluation attempt performed in Google Colab.

## Approach

1. Use Qwen2.5-VL-3B-Instruct as the base vision-language model.
2. Fine-tune the model using LoRA for the PPE-related task.
3. Load the fine-tuned adapter for inference.
4. Sample frames from a video and ask the model to identify PPE compliance.
5. Attempt to parse the model's responses into structured results for evaluation.

## Current Status

This repository documents an experimental proof of concept. Fine-tuning and inference were attempted, but the evaluation pipeline remains incomplete.

The inference attempt encountered problems with inconsistent or malformed JSON responses, including outputs wrapped in Markdown code fences and incomplete responses. Consequently, the generated evaluation results contained parsing errors and did not provide reliable accuracy metrics.

## Limitations

- **Unvalidated performance:** No reliable accuracy, precision, recall, or F1-score has been established.
- **Output formatting:** Model responses are not consistently compatible with the expected structured output format.
- **Incomplete evaluation:** Ground-truth labels and prediction parsing were not successfully integrated into a reliable evaluation pipeline.
- **Limited testing:** The experiments do not establish generalization across different cameras, lighting conditions, worker positions, or environments.
- **PPE detection reliability:** The model's ability to identify missing or incorrectly worn PPE has not been comprehensively validated.
- **Experimental deployment:** This work is not ready for production or safety-critical use.

## Future Improvements

- Enforce a consistent structured output schema and robustly handle invalid responses.
- Build a verified, frame-level ground-truth dataset.
- Evaluate performance using precision, recall, F1-score, and other suitable metrics.
- Test on diverse videos and challenging environmental conditions.
- Compare the VLM approach with dedicated object-detection models.

## Disclaimer

This repository records experimental development and its current limitations. Model outputs should not be treated as verified safety decisions or used as the sole basis for workplace safety enforcement.
