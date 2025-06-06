
# 🧠 CLIP-Powered Semantic Image Search – Marqo GCL Dataset (W-Fash 1M)

This project demonstrates a **semantic image retrieval engine** using **OpenAI's CLIP model** on the **W-Fashion 1M subset** of the [Marqo GCL dataset](https://marqo-gcl-public.s3.amazonaws.com/v1/marqo-gs-dataset.tar).

Given a **text query**, the system retrieves the most relevant **product images** from a large corpus using **zero-shot** vision-language embeddings.

---

## 📁 Project Structure

```
SEARCH-ENGINE-DSAI-COPY/
├── images_wfash/                  # Directory of extracted sample images
├── marqo_gs_wfash_1m/             # Corpus JSONs and ground truth CSVs
│   ├── corpus_1.json
│   ├── corpus_2.json
│   ├── query_0_product_id_0.csv   # In-domain queries & docs
│   ├── query_0_product_id_1.csv   # In-domain queries & novel docs
│   ├── query_1_product_id_0.csv   # Novel queries & in-domain docs
│   ├── query_1_product_id_1.csv   # Zero-shot queries & docs
├── clip_corpus1_embeddings.pt     # Precomputed CLIP image embeddings
├── main.ipynb                     # Notebook for retrieval & search
```

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/yusufimantaka/multimodal-searchengine.git
cd search-engine-dsai-copy
```

### 2. Download the Required Data

📦 **Corpus & Metadata:**

[Download marqo-gs-dataset.tar](https://marqo-gcl-public.s3.amazonaws.com/v1/marqo-gs-dataset.tar)

🖼️ **W-Fash Image Subset:**

[Download images_wfash.tar](https://marqo-gcl-public.s3.amazonaws.com/v1/images_wfash.tar)

🗂 Extract both into:

```
SEARCH-ENGINE-DSAI-COPY/
├── images_wfash/
├── marqo_gs_wfash_1m/
```

---

### 3. (Optional) Download Precomputed Embeddings

Instead of re-running slow inference, download the image embedding tensor:

📥 [Download from Google Drive](https://drive.google.com/drive/folders/1rBgahMi5CV1tiywlg_AJMJGmICIULzRz?usp=sharing)

Place this file in the root directory:
```
clip_corpus1_embeddings.pt
```

---

### 4. Run the Notebook

Launch the notebook to run:
- Text → Image search using CLIP
- Visualize top-k results
- Optional: Evaluate with ground-truth CSVs

```bash
jupyter notebook main.ipynb
```

---

## 🧠 Tools & Libraries

- [CLIP by OpenAI](https://github.com/openai/CLIP)
- PyTorch
- Pandas
- TQDM
- PIL / Matplotlib

---

## 🧪 Evaluation Splits (From CSVs)

The dataset follows Marqo’s **4 evaluation settings**:

| File Name                    | Query Type     | Document Type | Meaning          |
|-----------------------------|----------------|----------------|------------------|
| `query_0_product_id_0.csv`  | In-domain       | In-domain       | Normal setting   |
| `query_1_product_id_0.csv`  | Novel           | In-domain       | New query        |
| `query_0_product_id_1.csv`  | In-domain       | Novel           | New products     |
| `query_1_product_id_1.csv`  | Novel           | Novel           | Zero-shot test   |

Use these to test generalization capabilities of CLIP-based retrieval.

---

## 🤝 Acknowledgements

- [Marqo GCL Dataset](https://github.com/marqo-ai/marqo-gcl-dataset)
- [CLIP](https://github.com/openai/CLIP)

---

## 📄 License

This project is for educational and research purposes only. Refer to the original dataset licenses for usage terms and conditions.
