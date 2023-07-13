# QANet
A Pytorch implementation of [QANet](https://openreview.net/pdf?id=B14TlG-RW)  
The code is mostly based on the repository:
[andy840314/QANet-pytorch-](https://github.com/andy840314/QANet-pytorch-)

## Performance
|   Train DataSet    | Test DataSet | Training epochs |  EM  |  F1  |
|:------------------:|:------------:|:---------------:|:----:|:----:|
|     SQuAD 1.1      |  SQuAD 1.1   |       20        | 64.3 | 75.5 |
|     SQuAD 1.1      |    FinQA     |       20        | 2.17 | 10.1 |
|       FinQA        |    FinQA     |       20        | 15.2 | 15.2 |
| SQuAD 1.1 -> FinQA |    FinQA     |    20 -> 20     | 50.0 | 50.4 |

*These results are running with hidden size 96 with 1 attention heads and 8 batches.

## Requirements
  * python 3.6
  * pytorch 0.4.0
  * tqdm
  * spacy 2.0.11
  * tensorboardX
  * absl-py

## Usage
Download and preprocess the data
```bash
# download SQuAD and Glove
$ sh download.sh
# If cannot download the files, you may need to download them in online
```


Train the QAnet model with SQuAD dataset
```bash
# please clear the data files(not include folders) in the ./data path first
# preprocess SQuAD dataset
$ python main.py --mode data --model qanet
# model/model.pt will be generated every epoch
$ python main.py --mode train --model qanet
```
Test the QAnet model with SQuAD dataset
```bash
$ python main.py --mode test --model qanet
```

Train the QAnet model with FinQa dataset
```bash
# please clear the data files(not include folders) in the ./data path first
# preprocess FinQA dataset
$ python main.py --mode data --model finqa
# model/model.pt will be generated every epoch
$ python main.py --mode train --model finqa
```
Test the QAnet model with FinQa dataset
```bash
$ python main.py --mode test --model finqa
```
