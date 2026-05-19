# Arabic Sentence Segmentation Shared Task 2026

## Eval
We define Sentence segmentation as a **binary** token classification task. We use the following metrics:

* **Boundary Precision (P):** The percentage of predicted sentence boundaries that match a reference sentence boundary. Higher precision means fewer false boundary insertions.
* **Boundary Recall (R):** The percentage of reference sentence boundaries that are correctly predicted. Higher recall means fewer missed sentence boundaries.
* **Boundary F1 (F1):** The harmonic mean of boundary precision and boundary recall. It provides a single score that balances over-segmentation and under-segmentation errors.

We compute these metrics per document, and average across all documents in the split.

## Setup

You can set up the environment using either **Conda** or Python’s built-in **venv**.

### Option 1: Conda

Create and activate a new Conda environment:

```bash
conda create -n sent-seg python=3.10
conda activate sent-seg
```

### Option 2: venv

Create a virtual environment:
```bash
python -m venv .venv
```

Activate environment
```bash
# Mac/linux
source .venv/bin/activate

# Windows
.venv\Scripts\activate
```

Install required dependencies:
```bash
pip install -r requirements.txt
```

## Running Evaluation

Example inputs and outputs are available in the `examples/` subdirectory.

### Example command:
```bash
python scripts/eval.py \
    --task-name NoPnx-NP \
    --prediction-file-path examples/NoPnx-NP_example.csv \
    --output-file-path examples/ \
    --split test
```

The evaluation results are saved as:
```bash
{task_name}_{split}.json
```
