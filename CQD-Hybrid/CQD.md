This repository is based on the official implementation of CQD, [**Complex Query Answering with Neural Link Predictors**](https://openreview.net/forum?id=Mos9F9kDwkz).

```bibtex
@inproceedings{
    arakelyan2021complex,
    title={Complex Query Answering with Neural Link Predictors},
    author={Erik Arakelyan and Daniel Daza and Pasquale Minervini and Michael Cochez},
    booktitle={International Conference on Learning Representations},
    year={2021},
    url={https://openreview.net/forum?id=Mos9F9kDwkz}
}
```

In this work we present a variation of CQD, namely CQD-Hybrid, which reuses a pretrained link predictor to answer complex queries, by scoring atom predicates independently and aggregating the scores via t-norms and t-conorms, and additionally gives maximum score to the existing triples find in each query atom. 
We also added the code (in discrete.py and base.py) for answering 4p and 4i queries, namely a 4-path long sequence and an intersection of four links in the target variable.


We use the same pre-trained models available made available by the authors for CQD:

## 1. Download the pre-trained models

To download and decompress the pre-trained models, execute the following commands:

```bash
$ mkdir models/
$ for i in "fb15k" "fb15k-237" "nell"; do for j in "betae" "q2b"; do wget -c http://data.neuralnoise.com/kgreasoning-cqd/$i-$j.tar.gz; done; done
$ for i in *.tar.gz; do tar xvfz $i; done
```
## Evaluate the model
In job-FB15k237.sh, you find an example script used for evaluating CQD and CQD hybrid on the existing benchmarks, including their query reductions (as explained in the paper).
By setting the hyperparameter "cqd_max_norm=1'', you can will original CQD, while by setting, "cqd_max_norm=0.9" you will automatically use CQD-Hybrid, which will assign a score=1 to the existing triples.
For the foll list of hyperparameters for the old and new benchmarks please refer to the Appendix C of the paper.
