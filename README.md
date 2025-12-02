# Phone Recognition for Italian Dialects – Toy Corpus Experiment

This repository contains the full workflow, code, and data used to investigate whether automatic phone recognition (ZIPA) can complement or improve dictionary-based G2P phonetic transcription (phonItaliaR) for mainstream vs. non-mainstream (Sicilian) Italian speakers.  
This work was carried out as part of a BA thesis.

---

## 📁 Repository Structure

- mainstream/ - 10 audio files (mainstream Italian)
- non-mainstream/ - 10 audio files (Sicilian Italian)
- tc_sentences.csv - Metadata + orthographic sentences
- phonitalia_R.ipynb - Dictionary-based IPA pipeline (R)
- zipa_python.ipynb - ZIPA phone recognition (Python)
- compare.ipynb - PER computation + visualization
- dict_output.csv - Output of phonItaliaR IPA
- zipa_output.csv - Output of ZIPA inference
- comparison_results.csv - PER metrics
- per_phone_scatter.png - Final scatter plot


---

## 🎯 Research Goal

Standard Italian G2P dictionaries generate **canonical IPA transcriptions**, which may not reflect the actual pronunciations of **non-mainstream dialect speakers**.

This project asks:

> **Can an audio-based phone recognizer (ZIPA) complement or improve dictionary-based G2P transcription for dialectal speech?**

Workflow:

1. Generate canonical IPA using **phonItaliaR**  
2. Run ZIPA phone recognition on all audio files  
3. Tokenize and align sequences  
4. Compute **phone error rate (PER)**  
5. Compare mainstream vs. Sicilian speakers  

---

## 📚 Data: Toy Corpus (20 sentences)

The file:

- `tc_sentences.csv`

contains:

- `audio_file` — mp3 filename  
- `sentence_id` — IDs like `mainstream_s03` or `non_mainstream_s08`  
- `sentence` — orthographic transcription

Audio files are stored in:

- `/mainstream/`
- `/non-mainstream/`

---

## ▶️ How to Reproduce the Experiment

### 1. Dictionary IPA (R)

Run `phonitalia_R.ipynb`.

**Dependencies:**
- phonItaliaR  
- tidyverse  

**Output:** `dict_output.csv`

---

### 2. ZIPA Phone Recognition (Python)

Run `zipa_python.ipynb`.

**Dependencies:**
- torch  
- zipa  
- torchaudio  

**Output:** `zipa_output.csv`

---

### 3. PER Computation + Visualization

Run `compare.ipynb`.

**Dependencies:**
- pandas  
- matplotlib  
- python-Levenshtein (optional; custom fallback included)  

**Outputs:**  
- `comparison_results.csv`  
- `per_phone_scatter.png`

---

## 📊 Summary of Findings

- PER is **lower** for mainstream Italian speakers  
- PER is **higher** for Sicilian speakers  
- ZIPA shows clear performance differences across dialect groups  
- ZIPA may capture dialect-specific phonetic variation not represented in dictionary-based canonical transcriptions  

Further interpretation is provided in the thesis.
