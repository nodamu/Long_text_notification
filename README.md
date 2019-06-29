## Instructions for running training

* Clone official [bert_repo](https://github.com/google-research/bert)

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
    --num_train_epochs=3.0 
    --output_dir=../output/ \
    --do_lower_case=True \
```
### Requirements

 - **Tensorflow-gpu=1.12 or higher**
 