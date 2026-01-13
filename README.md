# multimodal-parkinsons-ai
# Multimodal Parkinson’s Disease Detection using Voice, Face & Hand Biomarkers

This repository presents a multimodal AI system for detecting Parkinson’s disease (PD) by integrating three independent physiological biomarkers:
- Voice (speech dysphonia)
- Face (micro-expressions & facial dynamics)
- Hand tapping (motor bradykinesia)

The system follows a biomarker-first design: each modality is modeled independently and then fused to study which signals contribute most to Parkinson’s classification.

---

##  Motivation

Parkinson’s disease is a progressive neurological disorder that affects speech, facial expressivity, and motor control long before clinical diagnosis.  
Most existing AI systems rely on a single modality, which leads to unstable and biased predictions.

This project investigates:
- Which biomarker is strongest?
- How much each modality contributes?
- Whether multimodal fusion improves reliability.

---

## 📂 Repository Structure
multimodal-parkinsons-ai/
├── notebooks/
│ ├── 01_voice_pipeline.ipynb # Speech-based PD detection
│ ├── 02_facial_pipeline.ipynb # Face-based PD detection
│ ├── 03_hand_tapping_pipeline.ipynb # Motor biomarker extraction
│ └── 04_multimodal_fusion.ipynb # Fusion & modality weight analysis
│
├── models/ # Trained neural networks
├── features/ # Extracted embeddings & PD scores
├── README.md
├── LICENSE
└── .gitignore


---

## 🔬 Modalities

### 1️⃣ Voice (Speech Dysphonia)
Acoustic features are extracted from sustained vowel recordings and fed into a neural network.  
A 32-dimensional embedding is learned and classified as Parkinson vs Healthy.

Notebook: `01_voice_pipeline.ipynb`

---

### 2️⃣ Face (Micro-expression & Motion)
Facial landmark-based features are embedded into a neural network that captures rigidity, blinking, and expression variability.

Notebook: `02_facial_pipeline.ipynb`

---

### 3️⃣ Hand Tapping (Motor Biomarker)
Finger tapping videos are processed using DeepLabCut to track finger trajectories.  
We extract:
- Tap rate
- Inter-tap interval
- Amplitude
- Fatigue trend

These are converted into a Parkinson risk score.

Notebook: `03_hand_tapping_pipeline.ipynb`

---

## 🔗 Multimodal Fusion

The three PD probability outputs are fused and compared using ROC-AUC.

Notebook: `04_multimodal_fusion.ipynb`

### 🔬 Experimental Setups
Seven experiments were performed:

| Experiment | Modalities |
|-----------|----------|
| 1 | Voice only |
| 2 | Face only |
| 3 | Hand only |
| 4 | Voice + Face |
| 5 | Voice + Hand |
| 6 | Face + Hand |
| 7 | Voice + Face + Hand |

---

## 📊 Results (ROC-AUC)

| Modality | ROC-AUC |
|--------|--------|
| Voice only | ~0.90 |
| Face only | ~0.50 |
| Hand only | ~1.00 |
| Voice + Face | ~0.69 |
| Voice + Hand | ~1.00 |
| Face + Hand | ~1.00 |
| All three | ~1.00 |

---

## 🧠 Key Findings

- Hand tapping is the strongest Parkinson biomarker.
- Voice adds robustness to predictions.
- Face alone is weak, but improves when combined.
- Multimodal fusion achieves near-perfect discrimination.

This confirms that Parkinson’s disease is best modeled as a **multimodal physiological disorder** rather than a single-signal problem.

---

## 🧪 Reproducibility

All notebooks are fully executable via the **Open in Colab** button on GitHub.  
Trained models and extracted features are provided.

---

## 👤 Author

**Jijnash Kumar**  
B.Tech (AI & ML)  
SRM Institute of Science and Technology  

Research Collaboration & Guidance:  
**Dr. Jitendra V. Tembhurne**  
Assistant Professor  
Department of Computer Science & Engineering  
Indian Institute of Information Technology (IIIT), Nagpur
---

## 📜 License

MIT License – free for academic and research use.

