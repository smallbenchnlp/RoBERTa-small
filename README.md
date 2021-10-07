## How to train RoBERTa-small model on a single GPU?

We used the run_mlm_no_trainer.py script from Hugging face [transformers](https://github.com/huggingface/transformers/tree/master/examples/pytorch/language-modeling) to pretrain a RoBERTa-small model for a single GPU. 

### Dataset 

Download the [openwebtext](https://skylion007.github.io/OpenWebTextCorpus/) data (12GB) and extract it (i.e., run tar xf openwebtext.tar.xz) . You will have txt files with the articles. 

### Preprocessing the dataset

The authors in [RoBERTa paper](https://arxiv.org/pdf/1907.11692.pdf) have used FULL-SENTENCES for their experiments. Please refer FULL-SENTENCES under section 4.2 in the paper. Preprocess the data in such a way that each article is written in one line and each of the articles are separated by a newline. Make sure the preprocessed data is in ```data/``` folder. 

For small bench NLP benchmark, we use the config as mentioned in ```/roberta-small/config.json``` . ```roberta-small```  has the tokenizer files and config files.

### Pretraining with run_mlm_no_trainer.py 

To train RoBERTa model from scratch, run this command, 

```
python run_mlm_no_trainer.py --model_type roberta --train_file /path/data/train.txt   //
--output_dir output --config_name /path/roberta-small --tokenizer_name /path/roberta-small 

```
