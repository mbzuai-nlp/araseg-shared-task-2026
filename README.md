# Arabic Sentence Segmentation Shared Task 2026
The Arabic Sentence Segmentation Shared Task 2026 will take place at the Fourth Arabic Natural Language Processing Conference (ArabicNLP 2026) at EMNLP 2026.

**Click here to [register for the shared task]()!**


## Task Description
The goal of this shared task is to segment Arabic documents into sentences. Given a document, systems must predict sentence boundaries to produce coherent sentences. The task is formulated as a binary classification task, where models predict whether a boundary follows each token.

## Data
**[The AraSeg Corpus](https://huggingface.co/collections/MBZUAI/arabic-sentence-segmentation-shared-task-2026)**:

## Shared Task Subtasks and Tracks
The shared task features **four** subtasks, each corresponding to an AraSeg corpus variant, with **two** tracks. The tracks impose different resource constraints. Participants can compete in one or more subtask and track.

* **Closed Track**: Models must be trained _exclusively_ on the AraSeg corpus.

   * No-Punctuation No-Paragraph (NoPnx-NP) Segmentation: [CodaBench Link]()
   * No-Punctuation Paragraph-Aware (NoPnx-PA) Segmentation: [CodaBench Link]()
   * No-Paragraph (NP) Segmentation: [CodaBench Link]()
   * Paragraph-Aware (PA) Segmentation: [CodaBench Link]()

* **Open Track**: No restrictions on external resources, allowing the use of any publicly available data.
   * No-Punctuation No-Paragraph (NoPnx-NP) Segmentation: [CodaBench Link]()
   * No-Punctuation Paragraph-Aware (NoPnx-PA) Segmentation: [CodaBench Link]()
   * No-Paragraph (NP) Segmentation: [CodaBench Link]()
   * Paragraph-Aware (PA) Segmentation: [CodaBench Link]()

With four subtasks and two tracks, the task results in **eight** possible combinations. Participants are allowed to compete in multiple subtasks and tracks.


## Evaluation
We define Sentence segmentation as a **binary** token classification task. We use the following metrics:

* **Boundary Precision (P):** The percentage of predicted sentence boundaries that match a reference sentence boundary. Higher precision means fewer false boundary insertions.
* **Boundary Recall (R):** The percentage of reference sentence boundaries that are correctly predicted. Higher recall means fewer missed sentence boundaries.
* **Boundary F1 (F1):** The harmonic mean of boundary precision and boundary recall. It provides a single score that balances over-segmentation and under-segmentation errors.

We compute these metrics per document, and average across all documents. We provide instructions on how to run the evaluation script below.

## Setup Requirements
You will need to have [conda](https://docs.conda.io/en/latest/miniconda.html) installed. To setup the environment, you would need to run:

```bash
git clone https://github.com/mbzuai-nlp/araseg-shared-task-2026
cd araseg-shared-task-2026

conda create -n araseg python=3.10
conda activate araseg

pip install -r requirements.txt
```

## Running the Evaluation

To evaluate your predictions, use the provided evaluation script. The script requires three arguments:
* `--output`: Path to your output CSV file containing predictions 
* `--task`: The data split to evaluate on (`Dev` or `Test`).
* `--split`: The task type ().


The evaluation results are saved as:
```bash
{task_name}_{split}.json
```
