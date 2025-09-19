INNAR: Intelligence Known and Novel Aircraft Recognition
=======================================================

This repository presents our work on aircraft recognition using a combination of known and novel class experimentation.  
We developed a cleaned dataset, performed extensive experiments on Kaggle, and explored methods to recognize aircraft classes beyond traditional classification.

-------------------------------------------------------
Dataset: MTARSI-INNAR
-------------------------------------------------------

We curated and cleaned the MTARSI-INNAR dataset, removing duplicates and inconsistencies.  

- Total Classes: 43  
- Total Images: 9,835  
- Status: Cleaned and deduplicated  

Link: https://zenodo.org/records/10421449

-------------------------------------------------------
Kaggle Experimentation
-------------------------------------------------------

We performed experimentation on Kaggle in the following notebook:  
Link: https://www.kaggle.com/code/haashaatif/innar-intelligent-known-and-novel-aircraft-recogn/edit 

This notebook requires two datasets:  

1. Training + Development Set  
   - Total Classes: 27  
   - Link: https://www.kaggle.com/datasets/khalidsaeed2022/train-embedder/data

2. Novel Set  
   - Total Classes: 16  
   - Link: https://www.kaggle.com/datasets/khalidsaeed2022/novel16/data

Further details of class splits and dataset partitioning can be found in our paper.

-------------------------------------------------------
Experiment Configuration
-------------------------------------------------------

The experimentation pipeline can be customized using the following configuration dictionary:
```python
config = {
    "base_dir":"/kaggle/input/train-embedder",
    "test_dir":"/kaggle/input/novel16",
    "optimizer":{
        "name":"adam",
        "learning_rate":1e-4,
    },
    "train_batch_size":8,
    "test_batch_size":64,
    "img_size":(224,224),
    "loss":"tripletmarginloss",
    "architecture":"efficientnet-b3",
    "embedding_dim":512,
    "device": torch.device("cuda:0" if torch.cuda.is_available() else "cpu"),
    "epochs": 10,
    "num_workers":2,
    "warmup_factor" : 10,
    "warmup_epoch" : 3,
    "accum_iter" : 8,
    "K":5,
    "num_triplets" : 10000,
    "validation-27-unknown":['ATR_72_ASW','KC-767_Tanker','C-130_Hercules','B-2_Spirit','F-16_Falcon'],
    "test-16-Novel":['E-2_Hawkeye', 'C-295M_CASA_EADS', 'Su-37_Flanker']
}
```

This configuration enables modification of:
- Number of novel classes
- Training/development and test splits
- Model architecture, embedding dimensions, and optimization parameters

-------------------------------------------------------
Citation
-------------------------------------------------------

If you use MTARSI-INNAR or our experimentation setup in your research, please cite our work.

-------------------------------------------------------
Contributors
-------------------------------------------------------

- Ahmad Saeed
- Haasha Bin Atif
- Dr. Mohsin Bilal
- Dr. Usman Habib
