# Dataset Card for OnCoCo 1.0
```
---
pretty_name: OnCoCo 1.0
tags:
  - language-resource
  - counseling
  - social-work
  - bilingual
  - dataset
  - fine-grained-classification
language:
  - de
  - en
license: cc-by-sa-4.0
multilinguality: bilingual
annotations_creators:
  - professional-annotators
language_creators:
- expert-generated (synthetic data curated by professionals)
task_categories:
  - text-classification
task_ids:
  - multi-class-classification
size_categories:
  - 1K<n<10K
source_datasets:
  - original dialogues
---
```

## Dataset Summary

OnCoCo 1.0 is a bilingual (German–English) dataset for *fine-grained message classification* in online counseling conversations.  
It provides a detailed, hierarchical annotation system designed to capture the rich semantics of psychosocial counseling exchanges.

The corpus contains 2,778 messages created by professional counselors and students in social work and computer science.  
The messages were originally written in German and translated to English by GPT-4o, so it's 5,556 samples in total.
Each message is labeled with one of 38 counselor or 28 client message categories, reflecting *impact factors*, *motivation*, *problem analysis*, and *resource activation*.

Unlike existing datasets such as MISC, MITI, or ESConv, OnCoCo 1.0 focuses on text-based counseling and emphasizes the integrative nature of psychosocial practice across different methods (e.g., Motivational Interviewing, client-centered therapy).

All dialogues are synthetic but linguistically authentic, curated to ensure ethical soundness and representativeness without privacy risks.

---

## Supported Tasks and Leaderboards

### Task: Multi-Class Text Classification
Each message is associated with a fine-grained category label from a hierarchical scheme.

- **Counselor Messages:** 38 categories  
- **Client Messages:** 28 categories  
- **Languages:** German (original), English (translation)  
- **Task Objective:** Predict the correct message category given the text and speaker role.

### Example applications
- Automated content analysis in counseling and social work  
- Training and evaluation of conversational AI models  
- Educational feedback tools for counselor training  
- Research on empathy, motivation, and relationship-building in text-based counseling

---

## Languages

- **German (DE):** Original language of all texts  
- **English (EN):** Translated version using GPT-4o and manually verified by human reviewers  

---

## Dataset Structure

### Data Instances
Each record corresponds to one message (utterance) in a counseling conversation.


```json
{
  "id": 467,
  "code": "CO-IF-AC-RF-RC",
  "type": "CO", 
  "lang": "EN", 
  "text_en": "Counselor: Could you describe in more detail what is troubling you at the moment?",
  "category": "Impact factors → Analysis and clarification of problems → Request for concerns"
}
```

### Data Fields

| Field | Type | Description |
|--------|------|-------------|
| `id` | `int` | Unique identifier |
| `code` | `string` | Unique short hierarchical code (e.g., `CO-IF-AC-RF-RC`) |
| `type` | `string` | Counselor (`CO`) or client (`CL`) |
| `lang` | `string` | Language code of the message (`DE` or `EN`) |
| `text` | `string` | Message text prefixed by the write (counselor or client) |
| `category` | `string` | Human-readable full label of the category |

---

## Dataset Creation

### Curation Process
- Created by social scientists and trained online counselors.  
- Synthetic dialogues generated based on professional counseling principles and validated for authenticity.  
- Manual annotation with a hierarchical category system derived from Grawe (2000), Motivational Interviewing (Miller & Rollnick, 2012), and online counseling research.

### Annotation
- Conducted by 6 professional counselors and 5 trained students.  
- Guidelines followed *Mayring’s (2015) qualitative content analysis* framework.  
- Intercoder reliability between best model and human coders: Cohen’s κ = 0.88.  

### Ethical Considerations
- No real client data used; all texts are simulated and anonymized by design.  
- Dataset contains no personal or sensitive information.  
- Ethical publication approved within research group’s institutional framework.

---

## Preprocessing

- All messages cleaned, tokenized, and translated.  
- Special tokens (`Counselor:` / `Client:`) optionally prepended during model training.  
- UTF-8 encoded JSON and CSV files provided.

---

## Licensing Information

- **License:** [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
  (Creative Commons Attribution–ShareAlike 4.0 International)
- **Copyright:** © 2025 Jens Albrecht, Robert Lehmann, Aleksandra Poltermann, Eric Rudolph, Philipp Steigerwald, Mara Stieler
- **Attribution:** When using this dataset, please attribute as follows:
  "OnCoCo 1.0 by Jens Albrecht, Robert Lehmann, Aleksandra Poltermann, Eric Rudolph, Philipp Steigerwald, and Mara Stieler (Technische Hochschule Georg Simon Ohm, Nuremberg), licensed under CC BY-SA 4.0"
- **ShareAlike clause:** Derivative datasets and models must retain the same license.

---

## Citation

If you use this dataset, please cite:

```
@misc{albrecht2025oncoco10publicdataset,
      title={OnCoCo 1.0: A Public Dataset for Fine-Grained Message Classification in Online Counseling Conversations}, 
      author={Jens Albrecht and Robert Lehmann and Aleksandra Poltermann and Eric Rudolph and Philipp Steigerwald and Mara Stieler},
      year={2025},
      eprint={2512.09804},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2512.09804}, 
}
```

---

## Dataset Curators

Developed by a multidisciplinary research team of social work and computer science experts at Technische Hochschule Georg Simon Ohm, Nuremberg, Germany:

- Jens Albrecht
- Robert Lehmann
- Aleksandra Poltermann
- Eric Rudolph
- Philipp Steigerwald
- Mara Stieler

**Contact:** Technische Hochschule Georg Simon Ohm, Kesslerplatz 12, 90489 Nuremberg, Germany

---

## Acknowledgements

This work was partially funded by a research grant from the STAEDTLER foundation.

---

## Dataset Links

- [https://github.com/th-nuernberg/oncoco_v1_dataset](https://github.com/th-nuernberg/oncoco_v1_dataset)  
