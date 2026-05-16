# DSAI 413 — Assignment 2: Multi-Modal Chest X-Ray Intelligence System
## Complete Pipeline: Report Generation & RAG-Based Visual QA

---

### Architecture Overview

| Mode | Input | Pipeline | Output |
|------|-------|----------|--------|
| **Report Generation** | CXR Image | MedGemma-1.5-4B | Structured Radiology Report |
| **RAG-Based VQA** | CXR Image + Question | ColPali → MedGemma | Grounded Clinical Answer |

### Models Used
- **MedGemma-1.5-4B-IT** (`google/medgemma-1.5-4b-it`) — Medical Vision-Language Model (generation)
- **ColPali v1.2** (`vidore/colpali-v1.2`) — Multi-vector late interaction retrieval (mandatory)
- **CLIP ViT-L/14** (`openai/clip-vit-large-patch14`) — Single-vector retrieval (comparison baseline)

### Key Design Decisions
- **No External APIs** — All inference runs locally on device
- **4-bit Quantization** — Both MedGemma and ColPali fit on a T4 GPU (16 GB)
- **Google Drive Integration** — Models and data persist across sessions
- **Automatic QA Dataset** — Generated from MIMIC-CXR reports using clinical templates (no API needed)
- **Gradio Demo** — Native Colab-compatible UI with public sharing
- 
