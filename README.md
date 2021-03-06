## Instructions for running training

* Clone this repo

* cd bert

* Download [BERT-Base, Uncased: 12-layer, 768-hidden, 12-heads, 110M parameters](https://storage.googleapis.com/bert_models/2018_10_18/uncased_L-12_H-768_A-12.zip)

* Unzip uncased_L-12_H-768_A-12 into the root directory

* Run  
```shell
python run_classifier.py \
    --task_name=cola \
    --do_train=true \
    --do_eval=true \
    --do_predict=true \
    --data_dir=../data/ \
    --vocab_file=../uncased_L-12_H-768_A-12/vocab.txt \
    --bert_config_file=../uncased_L-12_H-768_A-12/bert_config.json \
    --init_checkpoint=../uncased_L-12_H-768_A-12/bert_model.ckpt \
    --max_seq_length=400 \
    --train_batch_size=8 \
    --learning_rate=2e-5 \
    --num_train_epochs=3.0 \
    --output_dir=../output/ \
    --do_lower_case=True \
```
### Tensorboard

To view progress in tensorboard enter the following command in terminal
``` shell
tensorboard --logdir=output_dir
```

### Requirements

 - **Tensorflow-gpu=1.12 or higher**
 

### View test results
```
df_results = pd.read_csv("bert_output/test_results.tsv",sep="\t",header=None)
df_results_csv = pd.DataFrame({'index':df_test[''],
                               'mode':df_results.idxmax(axis=1)})
 
# Replacing index with string as required for submission
df_results_csv['mode'].replace(0, 'worn',inplace=True)
df_results_csv['mode'].replace(1, 'failed',inplace=True)
df_results_csv['mode'].replace(2, 'inoperable',inplace=True)
df_results_csv['mode'].replace(3, 'damaged',inplace=True)


 
# writing into .csv
df_results_csv.to_csv('data/result.csv',sep=",",index=None)
```
