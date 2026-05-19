# Arabic Sentence Segmentation Shared Task 2026
The Arabic Sentence Segmentation Shared Task 2026 will take place at the Fourth Arabic Natural Language Processing Conference (ArabicNLP 2026) at EMNLP 2026.

**Click here to [register for the shared task]()!**


## Task Description
The goal of this shared task is to segment Arabic documents into sentences. Given a document, systems must predict sentence boundaries to produce coherent sentences. The task is formulated as a binary classification task, where models predict whether a boundary follows each token.

## Data
**[AraSeg](https://huggingface.co/collections/MBZUAI/arabic-sentence-segmentation-shared-task-2026)** is the first comprehensive benchmark for Arabic sentence segmentation. The corpus is designed to support research on sentence segmentation in Modern Standard Arabic (MSA), particularly in settings where punctuation is inconsistent, missing, or noisy. The dataset has four variants that differ in terms of paragraph structure and punctuation availability:

* **[PA](https://huggingface.co/datasets/MBZUAI/AraSeg-2026-Shared-Task-PA)**: the Paragraph-Aware (PA) variant of the corpus where paragraph boundaries are provided.
* **[NoPnx-PA](https://huggingface.co/datasets/MBZUAI/AraSeg-2026-Shared-Task-NoPnx-PA)**: the No-Punctuation Paragraph-Aware (NoPnx-PA) variant of the corpus where punctuation is removed but paragraph boundaries are retained.
* **[NP](https://huggingface.co/datasets/MBZUAI/AraSeg-2026-Shared-Task-NP)**:the No-Paragraph (NP) variant of the corpus where paragraph boundaries are removed.
* **[NoPnx-NP](https://huggingface.co/datasets/MBZUAI/AraSeg-2026-Shared-Task-NoPnx-NP)**:the No-Punctuation No-Paragraph (NoPnx-NP) variant of the corpus where punctuation and paragraph boundaries are removed.

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
We define sentence segmentation as a **binary** token classification task. We use the following metrics:

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
* `--predictions`: Path to your output CSV file containing predictions 
* `--task`: The data split to evaluate on (`dev` or `test`).
* `--split`: The segmentation task type (`PA` for Paragraph-Aware, `NP` for No-Paragraph, `NoPnx-PA` for No-Punctuation Paragraph-Aware, and `NoPnx-NP` for No-Punctuation No-Paragraph).


To evaluate your system's output, you would need to run:
`python scripts/eval.py --predictions /path/to/prediction_csv --task [PA|NP|NoPNX-PA|NoPNX-NP] --split [dev|test]` 

Example usage:
`python scripts/eval.py ` 

### Prediction Output CSV Format
Your output CSV file should have the following columns:
* `Document ID`: The unique identifier for each document.
* `Prediction`: Your predicted segmentation boundaries for each as token in the document. This **must** be represented as a **binary sequence of 0s and 1s** (e.g., 0010 for a document of 4 tokens).

**Example**:
| Document ID | Prediction |
|-------------|------------|
| doc_00f88da2b078        | 00111001001000001011          |
| doc_4f96c619afba        | 011010111010101         |
| ...         | ...        |

Make sure the IDs in your output file match exactly those in the provided split (dev or test) for the chosen task.

### Example Output
After running the evaluation script, you will see output similar to the following in your terminal:
```
```
Each metric reflects the performance of your predictions on the selected split and task.

## Organizers
[Mohammed Elkholy]()

[Khalid Elmadani](https://khalid-elmadani.github.io/)

[Nizar Habash](https://www.nizarhabash.com/)

[Bashar Alhafni](https://www.basharalhafni.com/)

## License

This repo is available under the MIT license. See the [LICENSE](LICENSE) for more info.
