# 📚 Sentence Pair Classification using RoBERTa

🎯 Project Objective:
This project fine-tunes the transformer-based `roberta-base` model on two NLP tasks:
1. Paraphrase Detection (MRPC dataset)
2. Entailment Recognition (RTE dataset)

Both tasks aim to classify relationships between sentence pairs using Hugging Face Transformers and Datasets.

---

🧪 Tasks & Datasets:

🔹 Task 1: Paraphrase Detection
- Dataset: Microsoft Research Paraphrase Corpus (MRPC)
- Goal: Predict if the second sentence is a paraphrase of the first.

🔹 Task 2: Entailment Recognition
- Dataset: Recognizing Textual Entailment (RTE)
- Goal: Predict if the second sentence logically follows from the first.

---

🧠 Model Training:

For each task, two RoBERTa models were fine-tuned:

1️⃣ Frozen Model
- Only classification head trained
- Epochs: 10–20 (with early stopping)
- Lower training time and parameters

2️⃣ Unfrozen Model
- All layers fine-tuned
- Epochs: 3–5 (careful not to overfit)
- Used lower learning rate for stability

---

📊 Performance Summary:

| Task | Model      | Accuracy | Precision | Recall  | F1 Score |
|------|------------|----------|-----------|---------|----------|
| MRPC | Frozen     | 0.6838   | 0.6838    | 1.0000  | 0.8122   |
| MRPC | Unfrozen   | 0.8775   | 0.8908    | 0.9355  | 0.9126   |
| RTE  | Frozen     | 0.5060   | 0.5052    | 0.9602  | 0.6621   |
| RTE  | Unfrozen   | 0.7148   | 0.7955    | 0.5344  | 0.6393   |

Best Results:
- MRPC: Unfrozen RoBERTa with 4 epochs (F1 = 0.91)
- RTE: Unfrozen RoBERTa with better balance across metrics

---

🔧 Hyperparameters Used:

- Learning Rate: 2e-5
- Batch Size: 32
- Optimizer: AdamW
- Frozen Model Epochs: 10–20
- Unfrozen Model Epochs: 3–5
- Early Stopping: Applied in both modes

---

🧮 Trainable Parameters:

| Model Type | Trainable | Total Params |
|------------|-----------|--------------|
| Frozen     | 592,130   | 124,647,170  |
| Unfrozen   | 124,647,170 | 124,647,170 |

---

🧠 Key Insights:
- Unfreezing all layers significantly improves performance, especially in small datasets like MRPC.
- Early stopping is essential to avoid overfitting.
- Precision-recall tradeoff should be closely monitored during fine-tuning.
- LoRA was not used, as training time per epoch was manageable.

---

📁 Files Included:
- `coded_sol.ipynb` — Full model code with results
- `report.pdf` — Summarized analysis and model performance
- `problem.pdf` — Assignment instructions

✍️ Author: Gopi Trinadh Maddikunta
