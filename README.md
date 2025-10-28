<h1 align="center">
  VLM Weed Framework
</h1>

<h2 align="center">
  Vision Language Models for Zero-Shot Weed  Detection and Visual Reasoning in UAV Based Precision Agriculture
  
</h2>




<div align="center">
  <a href="https://scholar.google.com/citations?user=g9gcbl0AAAAJ&hl=en&oi=ao">Muhammad Fahad Nasir</a> &nbsp;•&nbsp;
  <a href="https://scholar.google.com/citations?hl=en&user=fZkn9poAAAAJ">Mobeen ur Rehman</a> &nbsp;•&nbsp;
  <a href="https://scholar.google.com/citations?user=bCC3kdUAAAAJ&hl=en">Irfan Hussain</a> &nbsp;•&nbsp;
</div>

<h4 align="center">
  <a href="https://arxiv.org/"><b>Paper</b></a> &nbsp;•&nbsp; 
  <a href="https://www.youtube.com/@Dr._Irfan_Robotics_Lab_KU"><b>Video</b></a>
</h4>

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) &nbsp;&nbsp;&nbsp;&nbsp; <img height="65" alt="image" src="https://github.com/user-attachments/assets/f9af6b5d-b8f3-4ca9-9398-d1d01cea6262" />  &nbsp;&nbsp; <img height="65" alt="image" src="https://github.com/user-attachments/assets/5dd33fad-d340-4fa4-b47b-6b2c3e44819a"  />&nbsp;&nbsp; <img height="65" alt="image" src="https://github.com/user-attachments/assets/b50ab72b-f752-4941-9a6a-b0a0cfcecaa7" />

</div>

[cc-by-sa]: http://creativecommons.org/licenses/by-sa/4.0/
[cc-by-sa-shield]: https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg



# Overview
The study explores whether modern vision–language models (VLMs) can improve weed detection in crop fields using UAV imagery without extensive manual annotation. Six commercial VLMs: ChatGPT-4.1, ChatGPT-4o, Gemini Flash 2.5, Gemini Flash Lite 2.5, LLaMA-4 Scout, and LLaMA-4 Maverick were tested on drone images of soybean fields to assess weed presence, location, reasoning, crop growth stage, and type.

A new method, Error-Probing Prompting (EPP), was introduced to test each model’s ability to self-correct and reason under counterfactual assumptions. Performance was rated on interpretability metrics such as grounding, specificity, plausibility, non-hallucination, and actionability.

Key findings:

- Gemini Flash 2.5 achieved the best overall and most interpretable results.

- ChatGPT-4.1 showed the strongest reasoning but weaker detection.

- ChatGPT-4o offered a balanced trade-off.

- LLaMA-4 models underperformed in localization and detail.

- Gemini Flash Lite 2.5 was efficient but fragile under EPP testing.

Overall, the research shows that explainability and adaptability, rather than just model size, best predict VLM reliability for precision weed management with minimal annotation.

<img width="1124" height="425" alt="Cropped" src="https://github.com/user-attachments/assets/65422a2a-ac83-4bc8-a6e8-6fb27565ac1b" />


# Methodology
Weeds remain a major constraint to row-crop productivity, yet current deep learning approaches for UAV imagery often require extensive annotation, generalize poorly across fields, and provide limited interpretability. We investigate whether modern vision–language models (VLMs) can address these gaps in a zero-shot setting. Using drone images from soybean fields with ground-truth weed boxes, we evaluate six commercial VLMs, ChatGPT-4.1, ChatGPT-4o, Gemini Flash 2.5, Gemini Flash Lite 2.5, LLaMA-4 Scout, and LLaMA-4 Maverick under a unified prompt that elicits (i) weed presence, (ii) spatial localization, (iii) reasoning, (iv) crop growth stage, and (v) crop type. 
<img width="2507" height="942" alt="Figure (3) - Methodology" src="https://github.com/user-attachments/assets/f14c5d6e-68ef-4850-85f7-03f48c2d91c1" />


This repo contains three Jupyter notebooks to run zero‑shot weed detection on a folder of images using:
- **Google Gemini 2.5 (Flash / Flash‑Lite)** – `Models/Weed_VLM_Gemini.ipynb`
- **Meta LLaMA‑Vision via Together AI** – `Models/Weed_VLM_LLAMA.ipynb`
- **OpenAI GPT‑4o (Vision)** – `Models/Weed_VLM_OpenAI.ipynb`

The notebooks iterate over a folder of images, send each image and a fixed prompt to the selected model, and save structured results to CSV/Excel.

---

## 1) Repository layout

```
.
├─ Models/
│  ├─ Weed_VLM_Gemini.ipynb
│  ├─ Weed_VLM_LLAMA.ipynb
│  └─ Weed_VLM_OpenAI.ipynb
├─ data/
│  └─ Images/              # put all input images here (jpg/png/…)
├─ outputs/
│  ├─ WeedVLM_GPT_4o_outputs.csv          # OpenAI run
│  ├─ gemini_flash_LITE_25_Fixed_weed_results.xlsx  # Gemini run
│  └─ (additional CSVs as the notebooks write them)
├─ requirements.txt
└─ README.md
```

> If your notebooks currently reference absolute paths like `/Joint_Val` or `/WeedVLM_GPT_4o_outputs.csv`, update them to the relative repo paths shown above: `data/Joint_Val` and `outputs/...`.

---

## 2) Setup

**Python 3.10+ is recommended.**

```bash
# clone your repo then in the repo root:
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

pip install --upgrade pip
pip install -r requirements.txt
```

---

## 3) API keys (add once, used by the notebooks)

### In‑notebook placeholders (works but less secure)
- **Gemini notebook** looks for `GOOGLE_API_KEY` and may have a line like:
  ```python
  os.environ["GOOGLE_API_KEY"] = "AI...your_key..."
  ```
  Replace the value **or** prefer the env‑var method above.
- **Together/LLaMA notebook** has:
  ```python
  TOGETHER_API_KEY = ""
  ```
  Paste your key or use the env var and read it via `os.getenv("TOGETHER_API_KEY")`.
- **OpenAI notebook** has:
  ```python
  openai.api_key = "sk-..."
  ```
  Replace it or use `os.getenv("OPENAI_API_KEY")` and set `openai.api_key` from that.

---


## 4) How to run

Start Jupyter and run any notebook **top‑to‑bottom**:

```bash
jupyter lab
# or
jupyter notebook
```

Inside each notebook:
1. Confirm the **image folder** is correct (default: `data/Joint_Val`).
2. Confirm the **API key** is being read (either from env var or the inline placeholder).
3. Run all cells. The notebooks will iterate images, call the model, and save results.

### Outputs (by notebook)
- **OpenAI** → `outputs/WeedVLM_GPT_4o_outputs.csv` (two columns like: `Image, GPT_Response`)
- **Gemini** → `outputs/gemini_flash_LITE_25_Fixed_weed_results.xlsx` (and a CSV alongside if enabled; columns like: `Image, Gemini_Response`)
- **LLaMA (Together)** → `outputs/llama_results.csv` (example name; check the cell that calls `to_csv`)

> The Gemini notebook also writes Excel via `pandas.DataFrame.to_excel()`. We include `openpyxl` in `requirements.txt` to ensure this works.

---



# Results
<table>
  <thead>
    <tr>
      <th rowspan="2">Model</th>
      <th rowspan="2">WD Acc</th>
      <th rowspan="2">CG Acc</th>
      <th rowspan="2">CT Acc</th>
      <th colspan="5">Zero-Shot: Weed Localization Accuracy + VLM Reasoning (0–5)</th>
      <th rowspan="2">Self-Corr.</th>
      <th colspan="5">EPP: Weed Localization Accuracy + VLM Reasoning (0–5)</th>
    </tr>
    <tr>
      <th>Grounding</th>
      <th>Specificity</th>
      <th>Plausibility</th>
      <th>Non-Hall.</th>
      <th>Actionability</th>
      <th>Grounding</th>
      <th>Specificity</th>
      <th>Plausibility</th>
      <th>Non-Hall.</th>
      <th>Actionability</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>ChatGPT-4.1</b></td>
      <td>0.3083</td><td>0.1927</td><td>0.8322</td>
      <td>2.0294</td><td>1.9191</td><td><b>4.6985</b></td><td>4.9264</td><td>2.4411</td>
      <td><b>1.00</b></td>
      <td>1.0263</td><td>1.0098</td><td>3.7540</td><td><b>4.9409</b></td><td>1.6852</td>
    </tr>
    <tr>
      <td><b>ChatGPT-4o</b></td>
      <td>0.4489</td><td>0.7857</td><td>0.7103</td>
      <td>1.3737</td><td>1.2575</td><td>4.1767</td><td><b>4.9494</b></td><td>1.9141</td>
      <td>0.9917</td>
      <td>0.6413</td><td>0.6118</td><td>3.2827</td><td>4.7468</td><td>1.3417</td>
    </tr>
    <tr>
      <td><b>LLaMA-4 Scout</b></td>
      <td>0.1496</td><td>0.0023</td><td>0.3946</td>
      <td>1.4545</td><td>1.3333</td><td>4.1818</td><td>4.8787</td><td>1.9545</td>
      <td>0.6773</td>
      <td>0.7500</td><td>0.7830</td><td>2.9952</td><td>4.4811</td><td>1.2028</td>
    </tr>
    <tr>
      <td><b>LLaMA-4 Maverick</b></td>
      <td>0.4557</td><td><b>0.8705</b></td><td>0.5306</td>
      <td>1.5074</td><td>1.4378</td><td>4.2935</td><td>4.8557</td><td>2.0845</td>
      <td><b>1.0000</b></td>
      <td>0.4333</td><td>0.4416</td><td>3.1083</td><td>4.4916</td><td>1.1833</td>
    </tr>
    <tr>
      <td><b>Gemini Flash 2.5</b></td>
      <td><b>0.7460</b></td><td>0.0493</td><td>0.8753</td>
      <td>2.2431</td><td>2.0668</td><td>4.5379</td><td>4.8936</td><td>2.6200</td>
      <td>0.7857</td>
      <td><b>1.3977</b></td><td><b>1.4090</b></td><td>3.8068</td><td>4.5454</td><td><b>1.8863</b></td>
    </tr>
    <tr>
      <td><b>Gemini Flash Lite 2.5</b></td>
      <td>0.6825</td><td>0.0000</td><td><b>0.9048</b></td>
      <td>1.7076</td><td>1.5581</td><td>4.3820</td><td>4.7408</td><td>2.1794</td>
      <td>0.1142</td>
      <td>0.0000</td><td>0.0000</td><td>0.0000</td><td>0.0000</td><td>0.0000</td>
    </tr>
  </tbody>
</table>


## Acknowledgements
This publication is based upon work supported by the Khalifa University of Science and Technology under Award No. RC1-2018-KUCARS. 


## Bibtex
```
@article{Nasir2025agrisense,
      title={Vision–Language Models for Zero-Shot Weed Detection and Visual Reasoning in UAV-Based Precision Agriculture},
      author={Nasir, Muhammad Fahad, Rehman, Mobeen Ur, and Hussain, Irfan},
      journal={State Journal Name},
      volume={225},
      pages={113487},
      year={2025},
      publisher={Elsevier}
    }
