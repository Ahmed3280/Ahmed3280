<div align="center">

# Ahmed Akram

### AI/ML Engineer · Computer Vision · Generative AI · MLOps Engineering

Building production-grade machine learning systems, from fine-tuned diffusion models to agentic, multi-agent pipelines.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/ahm-akram)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:ahmedakram7800@gmail.com)

</div>

---

### 🎓 Recognition

- 🥇 **1st Place, AZEX'26** (Egyptian Engineers Syndicate, Software Track), for AINAI
- 🏅 **Ideal Student Award**, El-Shorouk Academy
- 🎓 **DEPI Program graduate**, Microsoft Machine Learning Track (Egypt's Ministry of Communications and Information Technology), completed scholarship
- IEEE Organizing Committee Member, ICAISET'26

---

### 🏆 Headline Projects

#### AINAI: AI-Powered Modest Fashion Platform

**The gap:** virtual try-on (VTON) diffusion models are trained almost entirely on Western fashion: fitted, short-sleeve, body-hugging garments. They don't generalize to modest fashion (abayas, kaftans, jalabiyas) with full-length, loose silhouettes, an underserved market across MENA and the Gulf.

**What I built:** fine-tuned CatVTON, a SOTA diffusion-based VTON model, using LoRA adapters on a custom MENA garment dataset to adapt the Western-trained backbone to this segment.

- Also built a RAG-powered agentic shopping assistant: Gemini 2.5 Flash driving a four-tool ReAct loop over the product catalog, with FAISS + sentence-transformers (all-MiniLM-L6-v2) for retrieval, recommending garments and answering styling questions conversationally
- Deployed on RunPod Serverless (A40 GPU) behind a FastAPI backend, containerized with Docker
- 🥇 1st Place, AZEX'26. AI Lead and Project Lead for a 7-person team

[**→ LoRA_Fashion repo**](https://github.com/Ahmed3280/LoRA_Fashion) (training loop, LoRA fine-tuning code)

---

#### PR_Reviewer: Multi-Agent PR Code Reviewer

A multi-agent system that reviews GitHub pull requests automatically: fetches a real PR diff via the GitHub API, runs it through three specialist agents in parallel, and a manager node synthesizes their findings into a structured verdict (APPROVE / REQUEST CHANGES / COMMENT).

**Architecture**
- Built on LangGraph's `StateGraph` with a shared, typed `ReviewState` (TypedDict) passed between nodes
- Three specialist agents (security, style, test coverage) fan out from `START` and run in parallel, not sequentially
- A manager node coordinates execution and merges agent outputs into the final verdict
- Refactored from sequential to parallel execution, cutting response time by roughly 66%

**Engineering details**
- Diff filtering strips lock files and auto-generated code before diffs reach the agents, a real signal-to-noise improvement
- A 90-second `asyncio.wait_for` timeout on the FastAPI review endpoint caps backend cost and runtime, separate from the 120-second frontend fetch timeout
- System prompts iterated to cap findings at 10 items and tighten output formatting

**Evaluation harness**
- 34 test cases: 25 synthetic bug-injected diffs across 6 bug types, plus 9 adversarial clean diffs to test for false positives
- Deterministic keyword-based scoring, no LLM judge
- Initial run hit 100% across the board, a signal the dataset was too easy rather than a result worth keeping. The eval set was hardened before reporting final numbers:

| Metric | Result |
|---|---|
| Security agent | 100% F1 |
| Style agent | 100% F1 |
| Test coverage agent | F1 improved 71.4% → 85.7% |
| Overall recall | 88% → 96% |
| False positive rate | 11.1% |

**Deployed end-to-end on AWS**
- Docker image built and pushed to Docker Hub (`ahmedakram2/pr-reviewer:latest`)
- Backend on EC2 (Ubuntu 24.04, t3.micro, eu-north-1), API keys passed as runtime env vars, never baked into the image
- React + Vite frontend built and hosted on S3 static website hosting
- Infra terminated after demo recording to control cost, redeployable from the Docker image above

[**→ PR_Reviewer repo**](https://github.com/Ahmed3280/PR_Reviewer)<br>
[**→ PR_Reviewer demo**](https://www.linkedin.com/posts/ahm-akram_langchain-langgraph-generativeai-ugcPost-7473336860979916801-pypx/?utm_source=share&utm_medium=member_desktop&rcm=ACoAAEPWV-gBgHDP4p_62oLfgS-vqdy4iKActkQ)

---

### 🧮 Fundamentals — ML From Scratch

Core ML algorithms re-implemented with raw NumPy — no `sklearn.fit()`, no autograd, every gradient and split derived and coded by hand. Built to prove mechanical understanding underneath the frameworks used in the projects above.

| Algorithm | Validated against sklearn |
|---|---|
| Linear Regression | California Housing — MSE within 0.02 of sklearn |
| Logistic Regression | Breast Cancer Wisconsin — 97.4% accuracy |
| KNN | Wine dataset — matched/exceeded sklearn (100% vs 97.2% at best K) |
| K-Means | Mall Customer Segmentation — Inertia 65.58 vs sklearn's 65.57 |
| Decision Tree | Breast Cancer Wisconsin — predictions matched sklearn exactly, sample-for-sample |
| Random Forest | Breast Cancer Wisconsin — 94.74% test accuracy vs sklearn's 95.61% |

[**→ ML_From_Scratch repo**](https://github.com/Ahmed3280/ML-From-Scratch)

---

### 📌 Other Projects

| Project | What it does |
|---|---|
| **[Image_Segmentation_with_UNet_PyTorch](https://github.com/Ahmed3280/Image_Segmentation_with_UNet_PyTorch)** | U-Net built from scratch (encoder-decoder, skip connections) for binary image segmentation, with mixed-precision training pipeline — 99.16% accuracy, 0.978 Dice score |
| **[ResNet9_Plant_Disease](https://github.com/Ahmed3280/ResNet9_Plant_Disease)** | Custom ResNet9 architecture built from scratch (no pretrained weights), trained with One-Cycle LR policy and gradient clipping — 99.14% validation accuracy on plant disease classification |
| **[ViT_PyTorch_Paper_Replicating_and_Pretrained_Models](https://github.com/Ahmed3280/ViT_PyTorch_Paper_Replicating_and_Pretrained_Models)** | Vision Transformer replicated from scratch in PyTorch, benchmarked against pretrained DEFAULT (97.66%) and SWAG (98.67%) weights |
| **[Hand_Gesture_ITI](https://github.com/Ahmed3280/Hand_Gesture_ITI)** | Real-time hand gesture recognition: MediaPipe landmark extraction + XGBoost classifier, 98.79% accuracy |

---

### 🧠 Tech Stack

**Core**

![Python](https://img.shields.io/badge/Python%203.11-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

**Generative AI & Computer Vision**

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![HuggingFace](https://img.shields.io/badge/🤗%20HuggingFace-FFD21E?style=flat-square&logoColor=black)
![Diffusers](https://img.shields.io/badge/🧨%20Diffusers-FFD21E?style=flat-square&logoColor=black)
![PEFT/LoRA](https://img.shields.io/badge/PEFT%2FLoRA-EE4C2C?style=flat-square)
![MediaPipe](https://img.shields.io/badge/MediaPipe-0097A7?style=flat-square)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-0E76A8?style=flat-square)

**LLMs & Agentic Systems**

![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square)
![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white)
![FAISS](https://img.shields.io/badge/FAISS-3776AB?style=flat-square)
![sentence-transformers](https://img.shields.io/badge/sentence--transformers-EE4C2C?style=flat-square)

**Backend & Deployment**

![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS%20(EC2%2FS3)-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![RunPod](https://img.shields.io/badge/RunPod%20Serverless-6E3AF2?style=flat-square)
![Cloudinary](https://img.shields.io/badge/Cloudinary-3448C5?style=flat-square&logo=cloudinary&logoColor=white)
