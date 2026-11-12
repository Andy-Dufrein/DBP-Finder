# DBP-Finder

## Introduction
DBP-Finder is an advanced deep learning tool designed for the precise identification of DNA-binding proteins (DBPs). Leveraging the power of state-of-the-art pretrained language models (PLMs), particularly Ankh, DBP-Finder accurately predicts DNA-binding proteins from protein sequence data. This tool empowers researchers to gain deeper insights into genetic regulation and protein function.

- Source code: [Andy-Dufrein/DBP-Finder](https://github.com/Andy-Dufrein/DBP-Finder)
- Classifier weights: [camelStyle/DBP-Finder](https://huggingface.co/camelStyle/DBP-Finder)

##  Installation

### Environment Setup:
```bash
git clone https://github.com/Andy-Dufrein/DBP-Finder.git
cd DBP-Finder
conda env create -f env.yaml
conda activate DBP-Finder
```

## Data

Sequence files belong in `data/fasta/`; CSV files containing identifiers, annotations, and labels belong in `data/embeddings/input_csv/`. Generated embeddings belong in `data/embeddings/ankh_embeddings/`, and predictions in `data/prediction/`.

| Dataset | Description | Fasta | CSV |
| --- | --- | --- | --- |
| `UniSwiss_large` | Main training set | `data/fasta/UniSwiss_large.fasta` | `data/embeddings/input_csv/UniSwiss_large.csv` |
| `PDB2272` | Main test set | `data/fasta/pdb2272.fasta` | `data/embeddings/input_csv/pdb2272.csv` |
| `TrEMBL/Swiss` | UniProtKB-based TrEMBL/Swiss benchmark | `data/fasta/TrEMBL_Swiss.fasta` | `data/embeddings/input_csv/TrEMBL_Swiss.csv` |
| `MEROPS/REBASE` | Database-based MEROPS/REBASE benchmark | `data/fasta/merops_rebase.fasta` | `data/embeddings/input_csv/merops_rebase.csv` |

## Usage

`Example.ipynb` demonstrates checkpoint download, inference, identifier-based joining, and metrics on the included PDB2272 benchmark

### Command

To execute the script, use the following command:

```bash
python3 -m training_pLM.inference <FASTA_FILE> <OUTPUT_NAME> [--gpu <GPU_ID>]
```

__Example__

From the ROOT directory:

```bash
python3 -m training_pLM.inference data/fasta/Human-dna-binders.fasta Human-dna-binders --gpu 0
```

__Output__

The output will be saved in the `data/prediction` directory with the filename `Human-dna-binders.csv`

### Input Requirements

Input sequences must be in FASTA __UniProt__ format.
Duplicate sequences and identifiers will be automatically removed.

## Citation

TBA