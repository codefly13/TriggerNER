# TriggerNER
Code for ACL 2020 paper [TriggerNER: Learning with Entity Triggers as Explanations for named Entity Recognition]().

In this paper, we introduce 'entity triggers', an effective proxy of human explanaations for facilitating label-efficient learning of NER models. 
We crowd-sourced 14k entity triggers for two well-studied NER datasets.
Our proposed model, name Trigger Matching Network, jointly learns trigger representations and soft matching module with self-attention such that can generalize to unseen sentences easily for tagging.
Expriments show that the framework is significantly more cost-effective such that usinng 20% of the trigger-annotated sentences can result in a comparable performance of conventional supervised approaches using 70% training data.

<p align="center"><img src="figs/REGD.jpg" width="800"/></p>

If you make use of this code or the rules in your work, please kindly cite the following paper:

```bibtex
@article{linandlee2020triggerner,
  title={TriggerNER: Learning with Entity Triggers as Explanations for Named Entity Recognition},
  author={Bill Yuchen Lin and Dong-Ho Lee and Ming Shen and Xiao Huang and Ryan Moreno, Prashant Shiralkar and Xiang Ren},
  booktitle={Proceedings of ACL},
  year={2020}
}
```

The code is based on https://github.com/allanj/pytorch_lstmcrf.

## Quick Links
* [Requirements](#Requirements)
* [Trigger Dataset](#Trigger-Dataset)
* [Train and Test](#train-and-test)


## Trigger Dataset


## Requirements
Python >= 3.6 and PyTorch >= 0.4.1
```bash
python -m pip install -r requirements.txt
```

## Train and Test
* Train/Test Baseline (Bi-LSTM / CRF with n % of training dataset) :
```
python naive.py --dataset CONLL --percentage 20
python naive.py --dataset BC5CDR --percentage 20
```

* Train/Test Trigger Matching Network in supervised setting :
```
python supervised.py --dataset CONLL
python supervised.py --dataset BC5CDR
```

* Train/Test Trigger Matching Network in semi-supervised setting (self-training) :
```
python semi_supervised.py --dataset CONLL
python semi_supervised.py --dataset BC5CDR
```