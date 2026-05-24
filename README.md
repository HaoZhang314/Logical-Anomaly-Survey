# Logical-Anomaly-Survey

![Last Updated](https://img.shields.io/badge/Last_Updated-2026.05-blue)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A curated list of papers, datasets, and resources for **Logical Anomaly Detection** in industrial visual inspection.

> **What are logical anomalies?** Unlike *structural anomalies* (scratches, dents, stains) that manifest as local texture defects, *logical anomalies* are violations of high-level semantic constraints — e.g., wrong component count, misplaced parts, type substitution, or missing pairings. Each local patch looks normal, but the global semantics break the rules.
>
> The concept was formally introduced in:
> *Bergmann et al., "Beyond Dents and Scratches: Logical Constraints in Unsupervised Anomaly Detection and Localization," IJCV 2022.*

---

## Table of Contents

- [📦 Datasets](#-datasets)
- [🔍 Detection Methods](#-detection-methods)
  - [Global Feature Modeling](#global-feature-modeling)
  - [Component-Aware Detection](#component-aware-detection)
  - [🌐 Language & Large Model Driven](#-language--large-model-driven)
    - [Language-Enhanced Detection](#language-enhanced-detection)
    - [Training-Free Large Model Reasoning](#training-free-large-model-reasoning)
    - [Fine-tuned Multimodal Models](#fine-tuned-multimodal-models)
- [🔬 Anomaly Synthesis for Logical Anomalies](#-anomaly-synthesis-for-logical-anomalies)
- [📊 Benchmark Results](#-benchmark-results)
- [🛠️ Related Resources](#️-related-resources)
- [🤝 Contributing](#-contributing)
- [License](#license)

---

## 📦 Datasets

| Dataset | Paper | Venue | Year | Description | Links |
|---|---|---|---|---|---|
| **MVTec LOCO AD** | Beyond Dents and Scratches | IJCV | 2022 | Primary logical + structural anomaly benchmark; 5 industrial categories, 3644 train / 1568 test images; defines quantity / position / type violations; introduces AU-sPRO metric | [[paper](https://link.springer.com/article/10.1007/s11263-022-01578-9)] [[dataset](https://www.mvtec.com/company/research/datasets/mvtec-loco)] |
| **VID-AD** | VID-AD: A Dataset for Image-Level Logical Anomaly Detection under Vision-Induced Distraction | arXiv | 2026 | 10 manufacturing scenarios, 5 capture conditions, 50 one-class tasks, 10,395 images; evaluates logical detection robustness under visual distractions | [[paper](https://arxiv.org/abs/2603.13964)] [[code](https://github.com/nkthiroto/VID-AD)] |

---

## 🔍 Detection Methods

### Global Feature Modeling

Methods that extend local feature frameworks with global branches, or model global statistical distributions, to capture image-level logical structure without explicit component parsing.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **LADMIM**: Logical Anomaly Detection with Masked Image Modeling in Discrete Latent Space | TMLR | 2026 | Masked image modeling in discrete latent space forces long-range dependency learning; first MIM-based logical AD method | [[paper](https://arxiv.org/abs/2410.10234)] [[code](https://github.com/SkyShunsuke/LADMIM)] |
| **BAAF**: Universal Transformation of One-Class Classifiers for Unsupervised Image Anomaly Detection | arXiv | 2026 | Bootstrap aggregation filtering transforms any one-class classifier into a fully unsupervised logical anomaly detector without retraining | [[paper](https://arxiv.org/abs/2602.13091)] |
| **LA-EAD**: Simple and Effective Methods for Improving Logical Anomaly Detection Capability | Sensors | 2025 | Reconstruction-difference constraint + dedicated logical detection module on top of EfficientAD backbone; 94.2% logical AUROC on MVTec LOCO | [[paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC12389957/)] |
| **SPACE**: SPAtial-Aware Consistency Regularization for Anomaly Detection | WACV | 2025 | Spatial consistency regularization in student-teacher framework; feature converter module improves sensitivity to logical positional violations | [[paper](https://ieeexplore.ieee.org/abstract/document/10943358)] |
| **Separating Novel Features** for Logical Anomaly Detection | arXiv | 2024 | Margin-based constraint on knowledge distillation to enlarge the feature gap for logical anomalies; reduces false negatives without retraining | [[paper](https://arxiv.org/abs/2407.17909)] |
| **ULSAD**: Revisiting Deep Feature Reconstruction for Logical and Structural Industrial Anomaly Detection | TMLR | 2024 | Attention-based global reconstruction loss extends DFR for logical AD; unified structural + logical detection in one model | [[paper](https://arxiv.org/abs/2410.16255)] [[code](https://github.com/sukanyapatra1997/ULSAD-2024)] |
| **PUAD**: Frustratingly Simple Method for Robust Anomaly Detection | ICIP | 2024 | OOD detection on aggregated global feature space; complements local reconstruction methods for logical anomalies with minimal overhead | [[paper](https://arxiv.org/abs/2402.15143)] |
| **EfficientAD**: Accurate Visual Anomaly Detection at Millisecond-Level Latencies | WACV | 2024 | Lightweight student-teacher + global autoencoder branch; handles both structural and logical anomalies at 2 ms inference latency | [[paper](https://arxiv.org/abs/2303.14535)] |
| **Set Features** for Fine-grained Anomaly Detection | arXiv | 2023 | Models each sample as a distribution of patch elements; density estimation on set-level features captures global compositional patterns for logical AD | [[paper](https://arxiv.org/abs/2302.12245)] |
| **GLCF**: Learning Global-Local Correspondence with Semantic Bottleneck for Logical Anomaly Detection | arXiv | 2023 | Dual-branch (local reconstruction + global semantic bottleneck via ViT) framework; global branch explicitly encodes image-level logical structure | [[paper](https://arxiv.org/abs/2303.05768)] |
| **GCAD**: Beyond Dents and Scratches — Logical Constraints in Unsupervised Anomaly Detection and Localization | IJCV | 2022 | Foundational work introducing logical anomalies; dual-branch baseline combining feature regression (structural) with global autoencoder (logical); introduces MVTec LOCO AD and AU-sPRO | [[paper](https://link.springer.com/article/10.1007/s11263-022-01578-9)] |

---

### Component-Aware Detection

Methods that explicitly detect and segment product components, then model inter-component relationships (count, position, pairing) to verify logical constraints.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **BUSSARD**: Normalizing Flows for Bijective Universal Scene-Specific Anomalous Relationship Detection | CVPR | 2026 | Normalizing-flow-based bijective mapping of component relationships; scene-specific relationship distribution modeling for training-free logical anomaly localization | [[paper](https://arxiv.org/abs/2603.16645)] |
| **ObjectCore**: Efficient Few-shot Logical Anomaly Detection using Object Representations | WACV | 2026 | Bipartite matching of object-level representations between reference and query; 80.8% logical AUROC on MVTec LOCO in 4-shot setting | [[paper](https://arxiv.org/abs/2504.17850)] [[code](https://github.com/MaticFuc/ObjectCore)] |
| **PyramidCore**: Feature Pyramids for Few-Shot Logical Anomaly Detection | MELECON | 2026 | Extends ObjectCore with multi-scale feature pyramid representations; improves few-shot logical detection by capturing component structure at multiple granularities | [[paper](https://ieeexplore.ieee.org/document/11418871)] |
| **AnomalyMoE**: Towards a Language-free Generalist Model for Unified Visual Anomaly Detection | arXiv | 2025 | Mixture-of-Experts routing at patch, component, and global levels; single language-free model for structural and logical AD across 8 datasets | [[paper](https://arxiv.org/abs/2508.06203)] |
| **SALAD**: Semantics-Aware Logical Anomaly Detection | ICCV | 2025 | Label-free semantic composition maps extracted from normal samples; composition branch models semantic relationships between parts; 96.1% logical AUROC on MVTec LOCO | [[paper](https://arxiv.org/abs/2503.11056)] [[code](https://github.com/MaticFuc/SALAD)] |
| **UniVAD**: A Training-free Unified Model for Few-shot Visual Anomaly Detection | CVPR | 2025 | Contextual component clustering (C3) + component-aware patch matching (CAPM) + graph-based component relationship modeling (GECM); training-free, cross-category | [[paper](https://arxiv.org/abs/2504.01543)] [[code](https://github.com/FantasticGNU/UniVAD)] |
| **UniAD**: Integrating Geometric and Semantic Cues for Unified Anomaly Detection | ACM MM | 2025 | Dual-branch teacher-student with structural teacher + logical teacher (component-aware attention over geometry and semantics); 93.7% logical / 93.2% structural AUROC | [[paper](https://dl.acm.org/doi/10.1145/3746027.3755422)] |
| **RelationAD**: Industrial Vision Anomaly Detection with Relation Expression Logic Constraints | ICSRS | 2025 | Relational feature decoupling loss + sparse relation graph attention; logical constraints expressed as typed relation triples | [[paper](https://ieeexplore.ieee.org/abstract/document/11422150)] |
| **CSAD**: Unsupervised Component Segmentation for Logical Anomaly Detection | BMVC | 2024 | Foundation-model-based unsupervised component segmentation (SAM + DINO) + patch histogram + LGST scoring; 95.3% logical AUROC on MVTec LOCO | [[paper](https://arxiv.org/abs/2408.15628)] |
| **Few-Shot Part Segmentation** Reveals Compositional Logic for Industrial Anomaly Detection | AAAI | 2024 | Few-shot component segmentation + three memory banks (histogram, composition, patch features); 98.1% logical AUROC on MVTec LOCO — current highest reported | [[paper](https://ojs.aaai.org/index.php/AAAI/article/view/28703)] |
| **ComAD**: Component-aware Anomaly Detection Framework for Adjustable and Logical Industrial Visual Inspection | Adv. Eng. Informatics | 2023 | Configurable component parsing + metrological feature modeling; supports user-defined logical inspection rules | [[paper](https://doi.org/10.1016/j.aei.2023.102161)] [[code](https://github.com/liutongkun/ComAD)] |

---

### 🌐 Language & Large Model Driven

Methods in this group share a common thread: they leverage language, text priors, or large pre-trained models (VLMs, LLMs, MLLMs) as central components for detecting or explaining logical anomalies. We distinguish three sub-tracks by the role and integration depth of these models:

- **Language-Enhanced Detection** — text or vision-language alignment used as a *prior or feature*; the detection logic is not driven by LLM generation or reasoning.
- **Training-Free Large Model Reasoning** — powerful VLMs or LLMs invoked *as-is* (no task-specific fine-tuning) to reason about constraints, generate questions, or produce diagnostic chains.
- **Fine-tuned Multimodal Models** — MLLMs *fine-tuned* specifically for logical anomaly detection via SFT, GRPO, or other alignment strategies.

#### Language-Enhanced Detection

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **TMUAD**: Enhancing Logical Capabilities in Unified AD Models with a Text Memory Bank | arXiv | 2025 | Three-memory framework (class-level text descriptions + object-level + patch-level); text memory encodes normal object categories, counts, positions, and sizes; 91.8% logical AUROC | [[paper](https://arxiv.org/abs/2508.21795)] [[code](https://github.com/SIA-IDE/TMUAD)] |
| **CALIT**: Logical Anomaly Detection with Text-based Logic via Component-Aware Contrastive Language-Image Training | KDD | 2025 | CLIP-based component-aware contrastive training; text-format logical rules encoded as visual-semantic constraints; end-to-end training without explicit component annotations | [[paper](https://dl.acm.org/doi/10.1145/3711896.3737032)] |
| **SAM-LAD**: Segment Anything Model Meets Zero-Shot Logic Anomaly Detection | arXiv | 2025 | SAM-based zero-shot object matching + dynamic channel graph attention; text-guided component identification without product-specific training | [[paper](https://arxiv.org/abs/2406.00625)] |

#### Training-Free Large Model Reasoning

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **LogiDiag**: Diagnostic Planner-Guided Reasoning With LLMs for Logical Anomaly Diagnosis | IEEE TII | 2026 | LLM-based diagnostic planner generates structured step-by-step anomaly diagnosis reports; guides root-cause reasoning without task-specific fine-tuning | [[paper](https://ieeexplore.ieee.org/document/10840370)] |
| **Explainable Detection** of Logical and Structural Anomalies Based on MLLMs | RCVIS | 2026 | GPT-4o visual QA for logical anomaly detection; analyzes model limitations in quantity, position, and size perception; training-free | [[paper](https://link.springer.com/chapter/10.1007/978-3-032-00986-9_22)] |
| **LAKE**: Latent Anomaly Knowledge Excavation — Unveiling Sparse Sensitive Neurons in VLMs | arXiv | 2026 | Training-free; identifies anomaly-sensitive sparse neurons in pre-trained VLMs using minimal normal samples as calibration | [[paper](https://arxiv.org/abs/2604.07802)] |
| **LogicQA**: Logical Anomaly Detection with Vision Language Model Generated Questions | ACL Industry | 2025 | VLM auto-generates question lists covering logical constraints; visual QA over each question; training-free with natural language explanations; 87.6% logical AUROC | [[paper](https://aclanthology.org/2025.acl-industry.29/)] |
| **LogSAD**: Towards Training-free Anomaly Detection with Vision and Language Foundation Models | arXiv | 2025 | Match-of-thought architecture with GPT-4V; multi-granularity detection; compositional rule chains for logical reasoning; unified training-free framework | [[paper](https://arxiv.org/abs/2408.04293)] [[code](https://github.com/zhang0jhon/LogSAD)] |
| **GPT-LAD**: Leveraging Large Multimodal Models for Logical Anomaly Detection | ICASSP | 2025 | Mimics human inspection by prompting GPT-4V to define normality criteria; combines criteria-guided VLM judgment with CNN-based structural detection | [[paper](https://ieeexplore.ieee.org/abstract/document/10888757)] |
| **LogiCode**: An LLM-Driven Framework for Logical Anomaly Detection | arXiv | 2024 | LLM generates executable Python code to verify logical constraints (count, position, missing elements); introduces LOCO-Annotations and LogiBench evaluation protocol | [[paper](https://arxiv.org/abs/2406.04687)] |

#### Fine-tuned Multimodal Models

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **VLLM-LAD**: Visual Large Language Model for Zero-shot Logical Anomaly Detection | IEEE TCSVT | 2026 | Mipha-LoRA fine-tuned VLM; LDVP (local detail visual prompting) + GSFF (global semantic feature fusion) + G-L-R contrastive learning; **96.6% logical AUROC** on MVTec LOCO | [[paper](https://ieeexplore.ieee.org/document/10962044)] |
| **Interpretable LAC**: Interpretable Logical Anomaly Classification via Constraint Decomposition and Instruction Fine-Tuning | arXiv | 2026 | Decomposes logical constraints into atomic verifiable subqueries; CoT supervision + difficulty-aware resampling for instruction fine-tuning | [[paper](https://arxiv.org/abs/2602.03530)] |
| **EMIT**: Enhancing MLLMs for Industrial Anomaly Detection via Difficulty-Aware GRPO | arXiv | 2025 | Difficulty-aware GRPO training for MLLMs; soft prompt + heatmap-guided contrastive embeddings; +7.77% improvement on MMAD benchmark | [[paper](https://arxiv.org/abs/2507.21619)] |
| **AnomalyR1**: A GRPO-based End-to-end MLLM for Industrial Anomaly Detection | arXiv | 2025 | End-to-end VLM-R1 + GRPO with novel ROAM reward metric; 3B-parameter model generates anomaly masks and natural language explanations jointly | [[paper](https://arxiv.org/abs/2504.11914)] |
| **LAD-Reasoner**: Tiny Multimodal Models are Good Reasoners for Logical Anomaly Detection | arXiv | 2025 | Qwen2.5-VL 3B fine-tuned with SFT + GRPO; matches 72B model performance; defines RLAD (reasoning-based logical AD) task formulation | [[paper](https://arxiv.org/abs/2504.12749)] |
| **LR-IAD**: Mask-Free Industrial Anomaly Detection with Logical Reasoning | ICDM | 2025 | Chain-of-thought + GRPO fine-tuning for mask-free logical reasoning; +36% accuracy over prior methods on MVTec AD | [[paper](https://ieeexplore.ieee.org/document/11391878)] |
| **LogicAD**: Explainable Anomaly Detection via VLM-based Text Feature Extraction | arXiv | 2025 | Trained AVLM + format embedding + logic reasoner module; 86.0% logical AUROC (F1-max 83.7%) on MVTec LOCO with per-anomaly text explanations | [[paper](https://arxiv.org/abs/2501.01767)] |

---

## 🔬 Anomaly Synthesis for Logical Anomalies

Methods for generating synthetic logical anomaly samples to address the scarcity of defect data. Synthesized samples are typically used to train or augment detection models from other sections.

| Paper | Venue | Year | Description | Links |
|---|---|---|---|---|
| **ComGEN**: Component-aware Unsupervised Logical Anomaly Generation for Industrial Anomaly Detection | arXiv | 2025 | Disentangles visual components; attention-guided residual mapping for realistic logical anomaly synthesis; generated samples improve downstream detection; 91.2% AUROC on MVTec LOCO when used for training | [[paper](https://arxiv.org/abs/2502.11712)] |
| **Background-Aware Defect Generation** for Robust Industrial Anomaly Detection | arXiv | 2025 | Background-aware diffusion model with disentanglement loss; separates background denoising from defect generation for more realistic synthesis | [[paper](https://arxiv.org/abs/2411.16767)] |
| **AnomalyXFusion**: Multi-modal Anomaly Synthesis with Diffusion | arXiv | 2024 | Multi-modal (image + text + mask) X-embedding for controllable anomaly synthesis; introduces MVTec Caption dataset | [[paper](https://arxiv.org/abs/2404.19444)] |
| **AnomalyFactory**: Regard Anomaly Generation as Unsupervised Anomaly Localization | arXiv | 2024 | Unifies anomaly generation and localization under the same architecture; supports cross-domain anomaly synthesis | [[paper](https://arxiv.org/abs/2408.09533)] |
| **LogicAL**: Towards Logical Anomaly Synthesis for Unsupervised Anomaly Localization | CVPRW | 2024 | First dedicated logical anomaly synthesis method; edge-manipulation framework breaks component-level constraints via region editing | [[paper](https://ieeexplore.ieee.org/document/10678520/)] |

---

## 📊 Benchmark Results

### MVTec LOCO AD — Image-Level AUROC (%)

| Method | Section | Venue | Year | Logical | Structural | Overall | Code |
|---|---|---|---|---|---|---|---|
| Few-Shot Part Seg. | Component-Aware | AAAI | 2024 | **98.1** | — | — | — |
| VLLM-LAD | Fine-tuned | TCSVT | 2026 | **96.6** | — | — | — |
| SALAD | Component-Aware | ICCV | 2025 | **96.1** | — | — | [code](https://github.com/MaticFuc/SALAD) |
| CSAD | Component-Aware | BMVC | 2024 | 95.3 | — | — | — |
| LA-EAD | Global Feature | Sensors | 2025 | 94.2 | — | — | — |
| UniAD | Component-Aware | ACM MM | 2025 | 93.7 | 93.2 | — | — |
| TMUAD | Lang-Enhanced | arXiv | 2025 | 91.8 | — | — | [code](https://github.com/SIA-IDE/TMUAD) |
| ComGEN | Synthesis | arXiv | 2025 | — | — | 91.2 | — |
| LogicQA | Training-Free | ACL | 2025 | 87.6 | — | — | — |
| LogicAD | Fine-tuned | arXiv | 2025 | 86.0 | — | — | — |
| ObjectCore | Component-Aware | WACV | 2026 | 80.8 *(4-shot)* | — | — | [code](https://github.com/MaticFuc/ObjectCore) |
| EfficientAD | Global Feature | WACV | 2024 | ~70 | ~90+ | — | — |

> ⚠️ Numbers are taken from original papers. Evaluation protocols differ across methods (e.g., some report only the logical subset; few-shot methods use additional reference images at test time). Direct comparison requires caution. A unified re-evaluation is planned as part of the companion survey paper.

---

## 🛠️ Related Resources

- [awesome-industrial-anomaly-detection](https://github.com/M-3LAB/awesome-industrial-anomaly-detection) — Comprehensive list for general industrial AD
- [awesome-anomaly-synthesis](https://github.com/M-3LAB/awesome-anomaly-synthesis) — Companion repo to the IAS survey
- [MVTec LOCO AD Dataset](https://www.mvtec.com/company/research/datasets/mvtec-loco) — Primary benchmark for logical anomaly detection
- [VID-AD Dataset](https://github.com/nkthiroto/VID-AD) — Logical AD under vision-induced distraction

---

## 🤝 Contributing

1. Fork this repo
2. Add your paper / resource in the appropriate section
3. Follow the existing format: `**MethodName**: Paper Title | Venue | Year | One-line description | [links]`
4. Submit a Pull Request

Please ensure:
- Papers are ordered by year (newest first) within each section
- Links point to real URLs (arXiv abs pages preferred)
- One-line descriptions are specific ("what problem / what innovation"), not generic ("a new method for anomaly detection")
- For the Language & Large Model Driven section, pick the sub-section that best reflects the model's role: *prior/feature* (Language-Enhanced) vs *zero-shot reasoning* (Training-Free) vs *fine-tuned end-to-end* (Fine-tuned)

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
