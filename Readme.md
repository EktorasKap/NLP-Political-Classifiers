# LLM Prompting Strategies for Political Clarity

This repository contains the code and analysis for classifying political discourse clarity using Large Language Models (LLMs). The project focuses on leveraging instruction-tuned models through advanced prompting techniques (Zero-shot, Few-shot, and Chain-of-Thought) rather than traditional gradient-based fine-tuning.

## Acknowledgments
This project was developed as part of the "Artificial Intelligence II: Deep Learning for Natural Language Processing" course (Spring Semester 2025-2026) at the **Department of Informatics and Telecommunications, National and Kapodistrian University of Athens (EKPA)**.

## Overview

Politicians frequently use evasion tactics during interviews. The goal of this project is to build a robust classifier that evaluates a politician's answer to a specific question and categorizes it into one of three classes:
*   **Clear Reply:** A direct, specific, and factual answer to the exact question asked.
*   **Ambivalent:** A vague, non-committal, or partial answer that addresses the topic but avoids a concrete commitment.
*   **Clear Non-Reply:** Completely dodges the question, changes the subject entirely, or attacks the opponent.

## Dataset

The analysis uses the **QEvasion (CLARITY)** dataset, consisting of political question-answer pairs. The dataset features a heavy class imbalance, accurately reflecting real-world political interviews where "Ambivalent" responses are the most common.

## Methodology

### Models Evaluated
To systematically analyze the impact of model scale on reasoning and instruction-following, the following models from the Qwen family were evaluated using 4-bit quantization (via `bitsandbytes`) for memory efficiency:
*   `Qwen/Qwen3.5-0.8B`
*   `Qwen/Qwen3.5-2B`
*   `Qwen/Qwen3.5-4B`

### Prompting Strategies
1.  **Zero-Shot Prompting:** Providing the model with strict classification rules and role-playing instructions.
2.  **Few-Shot Prompting:** In-context learning using selected examples representing the most common evasion types per class.
3.  **Few-Shot Chain-of-Thought (CoT):** Forcing the model to output a `Reasoning:` step before providing the final `Label:`, improving the model's ability to identify "Topic Matching" (where a politician talks about a topic without answering the specific constraint).


## Evaluation & Metrics

The system is evaluated using a detailed confusion matrix, Accuracy, Precision, Recall, and **F1-Score** (Primary Metric), alongside the Macro F1-Score to account for class imbalances. 

Detailed error analysis and ablation studies on the prompts are included in the main notebook to understand the fundamental sources of model errors and the distinct strengths of larger models vs. smaller ones.

## License & Acknowledgements

*   Data provided by the AILS Lab (NTUA) / CLARITY dataset.
*   Models accessed via the Hugging Face Transformers ecosystem.