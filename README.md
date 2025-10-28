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
Weeds remain a major constraint to row-crop productivity, yet current deep learning approaches for UAV imagery often require extensive annotation, generalize poorly across fields, and provide limited interpretability. We investigate whether modern vision–language models (VLMs) can address these gaps in a zero-shot setting. Using drone images from soybean fields with ground-truth weed boxes, we evaluate six commercial VLMs, ChatGPT-4.1, ChatGPT-4o, Gemini Flash 2.5, Gemini Flash Lite 2.5, LLaMA-4 Scout, and LLaMA-4 Maverick under a unified prompt that elicits (i) weed presence, (ii) spatial localization, (iii) reasoning, (iv) crop growth stage, and (v) crop type. We further introduce Error-Probing Prompting (EPP), a counterfactual follow-up that forces re-analysis under the assumption that weeds are present, and we quantify self-correction with expert-rated interpretability scores (Grounding, Specificity, Plausibility, Non-Hallucination, Actionability). Across models, Gemini Flash 2.5 delivers the most consistent zero-shot performance and highest interpretability, ChatGPT-4.1 provides the strongest reasoning but lower raw detection, ChatGPT-4o offers a balanced profile, and LLaMA-4 variants lag in localization and specificity. Gemini Flash Lite 2.5 is efficient but fails EPP stress tests, revealing brittle reasoning. Visual grounding analysis and a text-to-region overlap metric show that interpretability tracks spatial correctness. Results highlight that explainability and feedback-driven adaptability not scale alone best predict reliability for field deployment, and position VLMs as promising, low-annotation tools for precision weed management. 
<img width="2507" height="942" alt="Figure (3) - Methodology" src="https://github.com/user-attachments/assets/f14c5d6e-68ef-4850-85f7-03f48c2d91c1" />




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
