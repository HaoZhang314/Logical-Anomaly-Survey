# Logical-Anomaly-Survey

![Last Updated](https://img.shields.io/badge/Last_Updated-2026.04-blue)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A curated list of papers, datasets, and resources for **Logical Anomaly Detection** in industrial visual inspection.

> **What are logical anomalies?** Unlike *structural anomalies* (scratches, dents, stains) that manifest as local texture defects, *logical anomalies* are violations of high-level semantic constraints — e.g., wrong component count, misplaced parts, type substitution, or missing pairings. Each local patch looks normal, but the global semantics break the rules.
>
> The concept was formally introduced in:
> *Bergmann et al., "Beyond Dents and Scratches: Logical Constraints in Unsupervised Anomaly Detection and Localization," IJCV 2022.*

**Contributions welcome!** If you find a missing paper or resource, please open an issue or submit a PR.

---

## Table of Contents

- [Surveys \& Overviews](#-surveys--overviews)
- [Datasets](#-datasets)
- [Detection Methods](#-detection-methods)
  - [Feature Reconstruction](#feature-reconstruction)
  - [Component-Aware](#component-aware)
  - [Foundation Models / MLLM](#foundation-models--mllm)
  - [Logic-Driven / Neuro-Symbolic](#logic-driven--neuro-symbolic)
  - [Unified Detection](#unified-detection)
- [Anomaly Synthesis for Logical Anomalies](#-anomaly-synthesis-for-logical-anomalies)
- [Benchmark Results](#-benchmark-results)
- [Related Resources](#-related-resources)
- [Citation](#-citation)
- [License](#license)

---

## 📑 Surveys & Overviews

| Paper | Venue | Year | Links |
|---|---|---|---|
| A Survey on Industrial Anomalies Synthesis | arXiv | 2025 | [[paper](https://arxiv.org/abs/2501.03006)] [[code](https://github.com/M-3LAB/awesome-anomaly-synthesis)] |
| Foundation Models for Industrial Anomaly Detection Survey | arXiv | 2024 | [paper] |

---

## 📦 Datasets

| Dataset | Paper | Venue | Year | Description | Links |
|---|---|---|---|---|---|
| **MVTec LOCO AD** | Beyond Dents and Scratches | IJCV | 2022 | First logical + structural anomaly benchmark; 5 industrial categories, 3644 images; defines quantity / position / type violations | [[paper](https://link.springer.com/article/10.1007/s11263-022-01578-9)] [[dataset](https://www.mvtec.com/company/research/datasets/mvtec-loco)] |
| **VID-AD** | VID-AD: A Dataset for Image-Level Logical Anomaly Detection under Vision-Induced Distraction | arXiv | 2026 | 10 manufacturing scenarios, 5 capture conditions, 50 one-class tasks, 10395 images; tests logical detection under visual distractions | [[paper](https://arxiv.org/abs/2503.09940)] [[code](https://github.com/nkthiroto/VID-AD)] |
| **MVTec AD** | MVTec AD — A Comprehensive Real-World Dataset for Unsupervised Anomaly Detection | CVPR | 2019 | Classic structural anomaly benchmark; useful as a contrast baseline | [[paper](https://openaccess.thecvf.com/content_CVPR_2019/html/Bergmann_MVTec_AD_A_Comprehensive_Real-World_Dataset_for_Unsupervised_Anomaly_Detection_CVPR_2019_paper.html)] [[dataset](https://www.mvtec.com/company/research/datasets/mvtec-ad)] |
| **VisA-D&R** | Towards Zero-Shot Anomaly Detection and Reasoning with MLLMs | arXiv | 2025 | AD + reasoning benchmark with image-level reasoning instruction data | [[paper](https://arxiv.org/abs/2502.07601)] |

---

## 🔍 Detection Methods

### Feature Reconstruction

Methods based on feature reconstruction, knowledge distillation, and memory banks. Originally designed for structural anomalies; some recent works extend to logical anomalies via global branches.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **LADMIM**: Logical Anomaly Detection with Masked Image Modeling in Discrete Latent Space | arXiv | 2026 | Masked image modeling forces long-range dependency learning for logical AD | [paper] |
| **LA-EAD**: Simple and Effective Methods for Improving Logical Anomaly Detection Capability | Sensors | 2025 | Lightweight framework on top of EfficientAD; adds reconstruction difference constraint + logical detection module; 94.2 AUROC on LOCO | [paper] |
| **SPACE**: SPAtial-Aware Consistency Regularization for Anomaly Detection | WACV | 2025 | Spatial consistency regularization in student-teacher; feature converter module handles logical anomalies | [paper] |
| **Separating Novel Features** for Logical Anomaly Detection: A Straightforward yet Effective Approach | arXiv | 2024 | Margin-based constraint on knowledge distillation to reduce false negatives in logical AD | [paper] |
| **Revisiting DFR** (ULSAD): Revisiting Deep Feature Reconstruction for Logical and Structural Industrial Anomaly Detection | arXiv | 2024 | Extends DFR with attention-based global loss for logical AD; unified structural + logical detection | [[paper](https://arxiv.org/abs/2406.05876)] [[code](https://github.com/sukanyapatra1997/ULSAD-2024)] |
| **PUAD**: Frustratingly Simple Method for Robust Anomaly Detection | ICIP | 2024 | OOD detection on aggregated feature space for logical anomalies; complements reconstruction-based methods | [paper] |
| **EfficientAD**: Accurate Visual Anomaly Detection at Millisecond-Level Latencies | WACV | 2024 | Lightweight student-teacher + global autoencoder; handles both structural & logical anomalies; 2ms latency | [[paper](https://arxiv.org/abs/2303.14535)] |
| **Set Features** for Fine-grained Anomaly Detection | arXiv | 2023 | Models sample as distribution of elements; density estimation on set features for logical AD | [paper] |

### Component-Aware

Methods that explicitly model components and their relations to capture logical constraints.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **RelationAD**: Industrial Vision Anomaly Detection with Relation Expression Logic Constraints | ICSRS | 2025 | Teacher-student with relational feature decoupling loss; sparse relation graph attention | [paper] |
| **ComAD**: Component-aware Anomaly Detection Framework for Adjustable and Logical Industrial Visual Inspection | Adv. Eng. Informatics | 2023 | Segments products into components; models metrological features and relationships for logical AD | [[paper](https://doi.org/10.1016/j.aei.2023.102161)] [[code](https://github.com/liutongkun/ComAD)] |
| **CSAD**: Unsupervised Component Segmentation for Logical Anomaly Detection | BMVC | 2024 | Foundation-model-based unsupervised component segmentation + patch histogram + LGST; 95.3% AUROC on LOCO | [paper] |
| **Few-Shot Part Segmentation** Reveals Compositional Logic for Industrial Anomaly Detection | AAAI | 2024 | Few-shot component segmentation + three memory banks (histogram, composition, patch); 98.1% logical AUROC on LOCO | [paper] |
| **GCAD** (GLCF): Learning Global-Local Correspondence with Semantic Bottleneck for Logical Anomaly Detection | arXiv | 2023 | Two-branch (local + global) framework with semantic bottleneck via ViT for logical AD | [paper] |

### Foundation Models / MLLM

Methods leveraging pre-trained vision-language models or multimodal large language models.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **LAKE**: Latent Anomaly Knowledge Excavation: Unveiling Sparse Sensitive Neurons in VLMs | arXiv | 2026 | Training-free; identifies anomaly-sensitive neurons in pre-trained VLMs using minimal normal samples | [paper] |
| **BAAF**: Universal Transformation of One-Class Classifiers for Unsupervised Image Anomaly Detection | arXiv | 2026 | Bootstrap aggregation filtering; transforms one-class classifiers into fully unsupervised detectors; first unsupervised logical AD | [paper] |
| **Explainable Detection** of Logical and Structural Anomalies Based on MLLMs | RCVIS | 2026 | GPT-4o for visual QA-based anomaly detection; analyzes limitations in quantity/position/size perception | [paper] |
| **UniVAD**: A Training-free Unified Model for Few-shot Visual Anomaly Detection | CVPR | 2025 | Contextual component clustering + component-aware patch matching + graph modeling; training-free, cross-domain | [[paper](https://arxiv.org/abs/2504.01543)] [[code](https://github.com/FantasticGNU/UniVAD)] |
| **AnomalyMoE**: Towards a Language-free Generalist Model for Unified Visual Anomaly Detection | arXiv | 2025 | Mixture-of-Experts at patch/component/global levels; single model for all anomaly types across 8 datasets | [paper] |
| **TMUAD**: Enhancing Logical Capabilities in Unified AD Models with a Text Memory Bank | arXiv | 2025 | Three-memory framework (text + object + patch) for unified structural & logical AD | [[paper](https://arxiv.org/abs/2505.01045)] [[code](https://github.com/SIA-IDE/TMUAD)] |
| **SAM-LAD**: Segment Anything Model Meets Zero-Shot Logic Anomaly Detection | arXiv | 2025 | SAM-based zero-shot logical AD; object matching model + dynamic channel graph attention | [paper] |
| **GPT-LAD**: Leveraging Large Multimodal Models for Logical Anomaly Detection | ICASSP | 2025 | Mimics human reasoning by defining normality criteria; combines GPT-4V with CNN-based models | [paper] |
| **LogSAD**: Towards Training-free Anomaly Detection with Vision and Language Foundation Models | arXiv | 2025 | Match-of-thought architecture with GPT-4V; multi-granularity detection; training-free, unified framework | [[paper](https://arxiv.org/abs/2408.04293)] [[code](https://github.com/zhang0jhon/LogSAD)] |
| **UniAD**: Integrating Geometric and Semantic Cues for Unified Anomaly Detection | ACM MM | 2025 | Dual-branch teacher-student; structural teacher + logical teacher with component-aware attention; 93.7% logical AUROC | [paper] |

### Logic-Driven / Neuro-Symbolic

Methods that explicitly perform logical reasoning, often using LLMs/MLLMs as reasoning engines.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **Interpretable LAC**: Interpretable Logical Anomaly Classification via Constraint Decomposition and Instruction Fine-Tuning | arXiv | 2026 | Decomposes logical constraints into verifiable subqueries; CoT supervision + difficulty-aware resampling | [paper] |
| **ObjectCore**: Efficient Few-shot Logical Anomaly Detection using Object Representations | arXiv | 2026 | Few-shot logical AD via bipartite matching of object representations; 80.8% AUROC in 4-shot on LOCO | [[paper](https://arxiv.org/abs/2504.17850)] [[code](https://github.com/MaticFuc/ObjectCore)] |
| **LR-IAD**: Mask-Free Industrial Anomaly Detection with Logical Reasoning | ICDM | 2025 | CoT + GRPO; mask-free reasoning framework; +36% accuracy on MVTec AD over prior methods | [paper] |
| **EMIT**: Enhancing MLLMs for Industrial Anomaly Detection via Difficulty-Aware GRPO | arXiv | 2025 | Difficulty-aware GRPO for MLLMs; soft prompt + heatmap-guided contrastive embeddings; +7.77% on MMAD | [paper] |
| **AnomalyR1**: A GRPO-based End-to-end MLLM for Industrial Anomaly Detection | arXiv | 2025 | End-to-end VLM-R1 + GRPO with novel ROAM metric; 3B params, generates masks + explanations | [paper] |
| **LAD-Reasoner**: Tiny Multimodal Models are Good Reasoners for Logical Anomaly Detection | arXiv | 2025 | Qwen2.5-VL 3B + SFT + GRPO; matches 72B model performance; defines RLAD (reasoning logical AD) task | [paper] |
| **LogicQA**: Logical Anomaly Detection with Vision Language Model Generated Questions | ACL | 2025 | QA-format reasoning over logical constraints via VLM-generated questions | [paper] |
| **LogicAD**: Explainable Anomaly Detection via VLM-based Text Feature Extraction | arXiv | 2025 | AVLM + format embedding + logic reasoner; 86.0% AUROC on LOCO with anomaly explanations | [paper] |
| **LogiCode**: An LLM-Driven Framework for Logical Anomaly Detection | IEEE T-ASE | 2024 | LLM generates Python code to detect logical violations (count, missing elements); introduces LOCO-Annotations + LogiBench | [paper] |
| **SALAD**: Semantics-Aware Logical Anomaly Detection | arXiv | 2025 | Composition branch modeling semantic relationships; novel label-free composition map extraction; 96.1% AUROC on LOCO | [[paper](https://arxiv.org/abs/2503.11056)] [[code](https://github.com/MaticFuc/SALAD)] |

### Unified Detection

Frameworks designed to handle both structural and logical anomalies simultaneously.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **UniAD** | ACM MM | 2025 | Dual-branch teacher-student integrating structural + logical teachers (see Foundation Models section) | [paper] |
| **TMUAD** | arXiv | 2025 | Three-memory framework for unified detection (see Foundation Models section) | [[code](https://github.com/SIA-IDE/TMUAD)] |
| **AnomalyMoE** | arXiv | 2025 | MoE architecture across three semantic levels (see Foundation Models section) | [paper] |
| **ULSAD** (Revisiting DFR) | arXiv | 2024 | Unified DFR + attention-based global loss (see Feature Reconstruction section) | [[code](https://github.com/sukanyapatra1997/ULSAD-2024)] |
| **EfficientAD** | WACV | 2024 | Student-teacher + global autoencoder (see Feature Reconstruction section) | [paper] |

---

## 🔬 Anomaly Synthesis for Logical Anomalies

Methods for generating synthetic logical anomaly samples to address data scarcity.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **ComGEN**: Component-aware Unsupervised Logical Anomaly Generation for Industrial Anomaly Detection | arXiv | 2025 | Disentangles visual components; attention-guided residual mapping; 91.2% AUROC on LOCO | [paper] |
| **Background-Aware Defect Generation** for Robust Industrial Anomaly Detection | arXiv | 2025 | Background-aware diffusion; disentanglement loss separates background denoising from defect generation | [paper] |
| **AnomalyXFusion**: Multi-modal Anomaly Synthesis with Diffusion | arXiv | 2024 | Multi-modal (image + text + mask) X-embedding for anomaly synthesis; introduces MVTec Caption dataset | [paper] |
| **AnomalyFactory**: Regard Anomaly Generation as Unsupervised Anomaly Localization | arXiv | 2024 | Unified generation + localization with same architecture; cross-domain anomaly synthesis | [paper] |
| **LogicAL**: Towards Logical Anomaly Synthesis for Unsupervised Anomaly Localization | CVPRW | 2024 | Edge-manipulation framework; first dedicated logical anomaly synthesis method; breaks logical constraints via edge editing | [paper] |

---

## 📊 Benchmark Results

### MVTec LOCO AD — Image-Level AUROC (%)

| Method | Category | Year | Logical | Structural | Average | Code |
|---|---|---|---|---|---|---|
| SALAD | Logic-Driven | 2025 | 96.1 | — | — | [code](https://github.com/MaticFuc/SALAD) |
| Few-Shot Part Seg. | Component-Aware | 2024 | 98.1 | — | — | — |
| CSAD | Component-Aware | 2024 | TBD | TBD | 95.3 | — |
| LA-EAD | Feature Recon. | 2025 | 94.2 | — | — | — |
| UniAD | Unified | 2025 | 93.7 | 93.2 | — | — |
| ComGEN | Synthesis | 2025 | TBD | TBD | 91.2 | — |
| LogicAD | Logic-Driven | 2025 | 86.0 (F1:83.7) | — | — | — |
| ObjectCore | Logic-Driven | 2026 | 80.8 (4-shot) | — | — | [code](https://github.com/MaticFuc/ObjectCore) |
| EfficientAD | Feature Recon. | 2024 | ~70 | ~90+ | — | — |

> **Note**: Numbers are collected from original papers. Evaluation protocols may differ across methods. A unified re-evaluation is planned as part of our survey paper.

---

## 🛠️ Related Resources

- [awesome-industrial-anomaly-detection](https://github.com/M-3LAB/awesome-industrial-anomaly-detection) — Comprehensive list for general industrial AD
- [awesome-anomaly-synthesis](https://github.com/M-3LAB/awesome-anomaly-synthesis) — Companion repo to the IAS survey
- [MVTec LOCO AD Dataset](https://www.mvtec.com/company/research/datasets/mvtec-loco) — The primary benchmark for logical anomaly detection
- [VID-AD Dataset](https://github.com/nkthiroto/VID-AD) — Logical AD under vision-induced distraction

---

## 🤝 Contributing

1. Fork this repo
2. Add your paper / resource in the appropriate section
3. Follow the format: `**MethodName**: Paper Title | Venue | Year | One-line description | [links]`
4. Submit a Pull Request

Please ensure:
- Papers are ordered by year (newest first) within each section
- Links point to real URLs (arXiv abs pages preferred)
- One-line descriptions are specific ("what problem / what innovation"), not generic

---

## 📝 Citation

If you find this resource helpful, please consider citing our survey:

```bibtex
@article{logical_anomaly_survey_2026,
  title   = {A Survey on Logical Anomaly Detection: Methods, Benchmarks, and Future Directions},
  author  = {TBD},
  journal = {arXiv preprint},
  year    = {2026}
}
```

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
