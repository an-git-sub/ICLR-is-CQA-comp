# Is Complex Query Answering Complex?
The repo containes the benchamarks used for the paper "Is Complex Query Answering Complex?", submitted to ICLR 2025.

In the folder "old benchmarks" you can find a folder for each of the old benchmark FB15k-237 and NELL; each containing two additional folders "test-query-reduction", which contain a folder for each query type (e.g., 2p,3p,..) and the files for queries (test-queries.pkl) and answers (test-easy-answers.pkl, test-hard-answers.pkl),  and "test-query-card", which contains these information for each cardinality category and query reduction (see Appendix A). Note that to evaluate the filtered union queries (see Sec. 4 of the paper) you can refer to test-query-reduction/2u/2u (for 2u queries) and to test-query-reduction/up/ov (for up queries).

You can download the old CQA benchmarks here: http://snap.stanford.edu/betae/KG_data.zip  Moreover, each benchmark folder contains the files to_skip_train.pickle and to_skip_valid.pickle are dictionaries containing for each query atom (a,r,?x) the corresponding existing triples in train and train+valid, respectively, which are used for CQD-Hybrid. 


Moreover, the folder "new benchmarks" contains the script used to generate the new queries, and a folder for each new benchmark, namely FB15k-237+H, ICEWS18+H, NELL995+H, each of them containing a zip test and validation data (only for ICEWS18+H we created new test splits, as in Sec. 6 of the paper). Each folder contains the created full-inference queries. Note that 4i and 4p queries are arranged in separate files wrt the rest of the queries. Also note that 1p queries are not present in these files as they're the same used for the old benchmark (apart from ICEWS18+H which is newly created). For ICEWS18+H we also share the script used to generate the KG splits and the KG splits used to generate the queries.

The "CQD-Hybrid" folder contains our implementation of the model of the same name. For evaluating the other methods used in the paper we re-used the orginal GitHub implementation:
GNN-QE: https://github.com/DeepGraphLearning/GNN-QE
ULTRA-Query: https://github.com/DeepGraphLearning/ULTRA/tree/main/config/ultraquery 
ConE: https://github.com/MIRALab-USTC/QE-ConE/blob/main
For hyperparameters refer to Appendix C.
