# Cross-lingual Question Answering for African Languages


## Environment and Repository Setup

- Set up a virtual environment using Conda or Virtualenv or

    ```bash
    conda create -n xor_qa_venv python=3.9 anaconda
    conda activate xor_qa_venv
    ```
    or
    ```bash
    python3 -m venv xor_qa_venv
    source xor_qa_venv/bin/activate
    ```
- Clone the repo

    ```bash
    git clone https://github.com/ToluClassics/masakhane_xqa --recurse-submodules
    ```
- Install Requirements

    ```bash
    pip install -r requirements.txt
    ```
## Source Data

The English and French passages for this project are drawn from Wikipedia snapshots of 2022-05-01 and 2022-04-20 respectively, and are downloaded from the [Internet Archive](https://archive.org/) to enable open-domain experiments.
The raw documents can be downloaded from the following URLS:

- https://archive.org/download/enwiki-20220501/enwiki-20220501-pages-articles-multistream.xml.bz2
- https://archive.org/download/frwiki-20220420/frwiki-20220420-pages-articles-multistream.xml.bz2

## Processing dumps

The already processed dumps are available on HuggingFace 😊, It is recommended to use this exact corpora to be able to reproduce the baseline results.
To download:

- [English](https://huggingface.co/datasets/ToluClassics/masakhane_wiki_100/resolve/main/masakhane_wiki_100-english/corpus.jsonl)
- [French](https://huggingface.co/datasets/ToluClassics/masakhane_wiki_100/resolve/main/masakhane_wiki_100-french/corpus.jsonl)


However, to run the processing pipeline yourself; We adopt the same processing used in the [Dense Passage Retriever Paper](https://arxiv.org/pdf/2004.04906.pdf).
The pipeline has been bundled into this [script](scripts/download_process_dumps.sh). You can run using the code provided below:

```terminal
bash scripts/generate_process_dumps.sh /path/to/dir_containing_dumps
```

However, [this document](docs/process_wiki_dumps.md) provides a detailed break down of the individual steps.

## Retriever

### BM25