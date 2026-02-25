# On the Feasibility of Adapting Massively Pre-trained TTS to Thai: Insights from Limited-Resource Fine-Tuning

> **Anonymous submission to Interspeech 2026**

This repository contains the evaluation code, results, and audio samples accompanying the paper **"On the Feasibility of Adapting Massively Pre-trained TTS to Thai: Insights from Limited-Resource Fine-Tuning"**. 

## 📄 Abstract

Large-scale pre-trained speech models offer significant potential for enhancing Text-to-Speech (TTS) synthesis in low-resource languages. This project investigates the adaptability of a 17B parameter base model for Thai TTS under severe data constraints. We fine-tuned the model on TSynC2, a corpus comprising only 11 hours of reading speech, leveraging linguistic knowledge from a 5-million-hour pre-training corpus that includes limited Thai data. Evaluation was conducted using 2,500 utterances from TSynC1 for objective Word Error Rate (WER) analysis and subjective preference tests with Thai listeners. Results indicate a high WER and audible audio artifacts ("cracks") or repetition in the fine-tuned output, attributed to the insufficient fine-tuning data failing to cover the full range of Thai grapheme sequences. 

However, subjective assessments revealed that the fine-tuned model demonstrated improved prosody and preference in complex sentences compared to the base model, which retained basic intelligibility due to pre-training exposure. We conclude that while massive base models provide a robust foundation for Thai TTS, achieving high fidelity requires expanded fine-tuning datasets to mitigate acoustic artifacts and improve grapheme coverage. Future work will focus on data augmentation and parameter-efficient fine-tuning strategies.

## 📂 Repository Contents

This repository focuses on the **evaluation pipeline** and **results analysis**. 

- `Eval/objective/`: Scripts for calculating Word Error Rate (WER) using Whisper-large-v3.
- `Eval/subjective/`: Scripts for processing preference test data and MOS calculations.
- `samples/`: Selected audio samples comparing Base Model vs. Fine-tuned Model.

## ⚠️ Note on Fine-Tuning Code

The fine-tuning implementation used in this work is adopted from the official **Qwen3-TTS** repository. To maintain clarity and respect upstream licensing, the fine-tuning scripts are **not included** in this repository. 

- **Base Model:** Qwen3-TTS (17B)
- **Fine-tuning Repo:** [https://github.com/QwenLM/Qwen3-TTS](https://github.com/QwenLM/Qwen3-TTS)
- **Modification:** We implemented a custom Supervised Fine-Tuning (SFT) pipeline with word-boundary preprocessing (see paper Section 3.2 for details).



## 📊 Key Results

| Model Configuration | WER (%) | Preference (Complex Sentences) |
| :--- | :--- | :--- |
| Base Model (17B) | High | Baseline |
| Fine-tuned (11h) | High (Improved) | **Preferred** |

*Note: Detailed statistical analysis and error breakdowns are available in the paper.*

## 🎧 Audio Samples

Listen to the comparison between the Base Model and the Fine-tuned Model in the `samples/` directory. 
- **Sample 1 :** Name Entity - Place Of Interest (No significant difference)
- **Sample 5 :** Complex Narrative (Fine-tuned model shows improved prosody, but cut off)

<!--
## 📝 Citation

If you use this code or reference our findings, please cite the paper (upon acceptance):

```bibtex
@inproceedings{anonymous2026feasibility,
  title={On the Feasibility of Adapting Massively Pre-trained TTS to Thai: Insights from Limited-Resource Fine-Tuning},
  author={Anonymous},
  booktitle={Interspeech 2026},
  year={2026}
}
```
-->

## 📄 License

This evaluation code is released under the MIT License. The underlying models and datasets (TSynC1/TSynC2) are subject to their respective licenses.