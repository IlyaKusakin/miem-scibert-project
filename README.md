MIEM SciBERT is an open-source linguistic model built and trained on [PyTorch](https://pytorch.org).

MIEM SciBERT is designed for
* development of production ready apps for classification scientific texts,
* research of NLP tasks closely related to scientific texts.

## Quick Links

* [HuggingFace repo with model](https://huggingface.co/miemBertProject/miem-scibert-linguistic)
* [Project page at MIEM cabinet](https://cabinet.miem.hse.ru/#/project/371/)
* [Short note about project on the lab site](https://miem.hse.ru/edu/ce/cadsystem/da_short_text)

## Model usage

* Open [notebook with model usage example](https://drive.google.com/file/d/1UZVhmA9LHL6Zsji-_9i_eJILmjhEziQz/view?usp=sharing) at Google Colab
* Or run [scibert_ru_usage.ipynb](https://github.com/IlyaKusakin/miem-scibert-project/blob/main/scibert_ru_usage.ipynb)  localy 
  1. Clone this repo, install requirements and run code in any IDE with ipynb support
  2. Run to install all necessary libraries
    ```
    pip install -r requirements.txt
    ```
  3. Open notebook in IDE with ipynb support

## Python

Import transformers, torch and SciBert model for MLM task
```
from transformers import BertTokenizer, BertForMaskedLM
import torch

tokenizer = BertTokenizer.from_pretrained('miemBertProject/miem-scibert-linguistic')
model = BertForMaskedLM.from_pretrained('miemBertProject/miem-scibert-linguistic')
```

Import SciBert model to get tokens or texts embeddings
```
from transformers import BertModel

tokenizer = BertTokenizer.from_pretrained('miemBertProject/miem-scibert-linguistic')
model=BertModel.from_pretrained('miemBertProject/miem-scibert-linguistic')
model.eval()

input_ids = tokenizer("Сравнительное влияние климата и обновления культивации на урожайность риса в Китае", return_tensors="pt")["input_ids"]
outputs=model(input_ids)
```

## GRNTI classification

MIEM SciBERT linguistic model was fine-tuned for [GRNTI](https://grnti.ru/) classification task (about 70 classes at 1st level and 400+ classes at 2nd level of rubricator). 

* Detailed report about classification results [report](https://drive.google.com/drive/folders/1MbW6TUvDpnaRxBgdXOCHtzR1ohfLkiqr?usp=sharing) 
* Data example of short scientific texts that was classified [subsample_texts_short.csv](https://github.com/IlyaKusakin/miem-scibert-project/blob/main/subsample_texts_short.csv)
