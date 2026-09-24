# Ovis-Omni-Embedding
<div align="center">
  <img src=ovis_logo.png width="30%"/>
</div>
<br>

<p align="center">
  <a href="https://github.com/ATH-MaaS/Ovis-Omni-Embedding"><img src="https://img.shields.io/badge/GitHub-Ovis--Omni--Embedding-3157C8?logo=github" alt="github"></a>
  <a href="https://huggingface.co/ATH-MaaS/Ovis-Omni-Embedding-3B"><img src="https://img.shields.io/badge/🤗_Model_Page-Ovis--Omni--Embedding--3B-yellow" alt="model page"></a>
  <a href="https://arxiv.org/pdf/2609.25165"><img src="https://img.shields.io/badge/📖_Technical_Report-arXiv-b31b1b.svg" alt="technical report"></a>
</p>

## Introduction

Ovis-Omni-Embedding is an omni-modal embedding model developed by the Alibaba ATH-MaaS team. It maps heterogeneous modalities — including text, image, video, and audio — into a unified representation space, enabling comprehensive cross-modal retrieval and understanding within a single model.

**Ovis-Omni-Embedding-3B** achieves leading performance on the Massive Multimodal Embedding Benchmark (MMEB). It is a 3B-parameter universal embedding model for text, images, visual documents, video, audio, and interleaved multimodal inputs, and is initialized from **Qwen2.5-Omni-3B**. Rather than attaching separate modality-specific embedding towers, it retains the native text tokenizer, vision encoder, audio encoder, and shared Thinker backbone. The speech-generation Talker and language-modeling head are removed, and the final-layer hidden state at the last non-padding token is used directly as the retrieval embedding.

> Our technical report is now available on arXiv: [**arXiv:2609.25165**](https://arxiv.org/pdf/2609.25165). The model page is also live on Hugging Face: [**ATH-MaaS/Ovis-Omni-Embedding-3B**](https://huggingface.co/ATH-MaaS/Ovis-Omni-Embedding-3B). Model weights are not open-sourced yet and will be released in the near future. Stay tuned!

## Performance

### MMEB-v3

MMEB-v3 is an omni-modal benchmark comprising **190 datasets** across image, video, visual-document, text, audio, and agent retrieval. Ovis-Omni-Embedding-3B achieves **58.46 overall**, outperforming the strongest compared baseline by **5.19 points**, and ranks first on the aggregate score of every modality group.

| Group | Ovis-Omni-Embedding-3B | Best compared baseline | Margin |
|:------|:----------------------:|:----------------------:|:------:|
| Image | 77.55 | 73.83 | +3.72 |
| Video | 64.99 | 59.37 | +5.62 |
| Visual document | 78.26 | 75.37 | +2.89 |
| Text | 47.15 | 43.62 | +3.53 |
| Audio | 50.08 | 43.17 | +6.91 |
| Agent | 45.52 | 39.42 | +6.10 |
| **All 190 datasets** | **58.46** | 53.27 | **+5.19** |

Across the 31 aggregate and sub-task entries in the complete comparison, Ovis-Omni-Embedding-3B ranks first on 22 and second on 8. MultiConIR is the only entry on which it falls outside the top two.

### Additional benchmark results

| Benchmark | Ovis-Embedding-Omni-3B | Best compared baseline | Evaluation scope |
|---|---:|---:|---|
| MAEB (beta) | **57.29** | LCO-Embedding-Omni-7B: 53.54 | Mean over 30 audio embedding tasks |
| MVEB (beta) | **61.77** | LCO-Embedding-Omni-7B: 57.58 | Mean over 23 video and audio-video embedding tasks |
| RTEB | **67.35** | Qwen3-Embedding-4B: 67.27 | 15-task English public retrieval split |

These benchmark families use their own official aggregation procedures, so their scores should not be averaged together. MAEB and MVEB results are local evaluations inserted into the corresponding leaderboard snapshots, as described in the technical report.

## Release
- [26/09/23] 🔥 Our [technical report](https://arxiv.org/pdf/2609.25165) is out, and the model page of **Ovis-Omni-Embedding-3B** is now live on [Hugging Face](https://huggingface.co/ATH-MaaS/Ovis-Omni-Embedding-3B). Model weights will be open-sourced soon.
- [26/09/04] 🔥 **Ovis-Omni-Embedding-3B** released. Check out the [MMEB Leaderboard](https://huggingface.co/spaces/TIGER-Lab/MMEB) for results.
- [26/08/21] 🔥 **Ovis-Omni-Embedding-v0.5** released and submitted to the [MMEB](https://huggingface.co/spaces/TIGER-Lab/MMEB) official leaderboard.
- [26/07/30] 🔥 Announcing Ovis-Omni-Embedding, an omni-modal embedding model for text, image, video, and audio.

## Model

| Model | Parameters | Supported Modalities | Embedding Dim | Model Page | Tech Report |
|:------|:----------:|:--------------------:|:-------------:|:----------:|:-----------:|
| Ovis-Omni-Embedding-3B | 3B | Text / Image / Visual Document / Video / Audio | 2048 (elastic: 1024 / 512 / 256 / 128) | [🤗 HF](https://huggingface.co/ATH-MaaS/Ovis-Omni-Embedding-3B)  | [📖 arXiv](https://arxiv.org/pdf/2609.25165) |

## Related Projects
- [**Ovis-VL-Embedding**](https://github.com/ATH-MaaS/Ovis-VL-Embedding): A vision-language embedding model for text, image, visual document, and video.

## Citation
If you find this work useful, please consider citing our technical report: [arXiv:2609.25165](https://arxiv.org/pdf/2609.25165).

## License
This project is licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.txt) (SPDX-License-Identifier: Apache-2.0).

## Disclaimer
We used compliance-checking algorithms during the training process, to ensure the compliance of the trained model to the best of our ability. Due to the complexity of the data and the diversity of language model usage scenarios, we cannot guarantee that the model is completely free of copyright issues or improper content. If you believe anything infringes on your rights or generates improper content, please contact us, and we will promptly address the matter.
