# NoDaLiDa 2021 fin-sme NMT with backtranslations

This directory contains parallel training, development and test sets and [OpusFilter](https://github.com/Helsinki-NLP/OpusFilter) configuration files for creating backtranslations training sets as described in the [NoDaLiDa 2021 paper](https://aclanthology.org/2021.nodalida-main.37/).

## Data sets

The `data` directory contains parallel fin-sme data and monolingual sme data from <https://victorio.uit.no/freecorpus/>:

- finsme.fi-sme.fi finsme.fi-sme.se
- se_mono.txt

The `data` directory contains training, development and test sets created from the available parallel data:

- train.fi train.se
- dev.fi dev.se
- test.fi test.se

There is an additional small test sets consisting of YLE news articles:

- yle_testset.fi yle_testset.se

Backtranslation with NMT from the filtered and deduplicated `se_mono.txt` file:

- nmt_bt.translation.fi

Backtranslation with Apertium RBMT system. The line number of the RBMT bt files differ from the NMT bt files because the RBMT system failed to translate some sentences:

- apertium.fi, apertium.se

## Configuration files

The `create_train_dev_test_sets.yaml` is not needed to run as the results of this file are included in this directory. The config file creates training, development and test sets from the available parallel data. The train, dev and test sets in this directory are the exact same as used in the NoDaLiDa 2021 paper. If you run `create_train_dev_test_sets.yaml`, this will create new random train, dev and test sets.

To create all the training sets that include backtranslation as described in the paper, you need to run `create_bt_training_sets.yaml`. The created data sets are:

- nodup_nmt_all_bt.fi nodup_nmt_all_bt.se
- nodup_rbmt_all_bt.fi nodup_rbmt_all_bt.se
- nodup_nmt_all+rbmt_all_bt.fi nodup_nmt_all+rbmt_all_bt.se
- nodup_nmt_clean_bt.fi nodup_nmt_clean_bt.se
- nodup_rbmt_clean_bt.fi nodup_rbmt_clean_bt.se
- nodup_nmt_clean+rbmt_clean_bt.fi nodup_nmt_clean+rbmt_clean_bt.se
- nodup_nmt_clean+rbmt_clean_bt.fi nodup_nmt_all+rbmt_all_bt.se
