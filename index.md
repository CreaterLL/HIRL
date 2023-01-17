---
layout: default
---

## Hierarchical Invariant Learning for Domain Generalization Recommendation

## 1 Abstract

Domain generalization has been recently becoming an important task in machine learning. However, seldom work discusses the domain generalization task in recommendation systems. In this paper, we intend to figure out the domain generalization recommendation and propose corresponding models to deal with the task. We illustrate the domain generalization recommendation, figure out its pivotal properties, and give a clear symbolized defination on this setting. We demonstrate its strong connection with zero-shot recommendation, pretrained recommendation and cold-start recommendation, and distinguish it from content-based recommendation. Based on its properties, we propose HIRL+ and a series heuristic methods to sovle the task. We propose hierarchical invariant learning, in order to expel the specific patterns in both domain-level and environment-level to find the common patterns in the generalization space. We propose the learnable environment assignment mechnisms to make environments more flexible, fine-grained and balance. We propose an adversarial environment refinement mechnism based on adversarial training to improve the robustenss against distribution shifts inside the domain generalization process. We conduct experiments on real-word datasets to verify the effectiveness of our models, and carry out further studies on domain distance and domain diversity. We intend to open up and discuss the domain generalization recommendation setting with corresponding models, and we publish our project on https://anonymous-hirl.github.io/HIRL.

## 2 Contributions

In conclusion, the main contributions of this paper can be summarized as follows:

- We give a clear defination of domain generalization recommendation, which can be considered as a new type of method for cold-start problem, pretrained recommendation problem and zero-shot recommendation problem.

- We prepose HIRL to obtain more common and significant pattens on more fine-grained environment level. We propose environment assignment mechanism to make environment flexible and learnable. We further improve robustness aginst distribution mismatch by proposing environment refinement mechanism. We combine the three components as HIRL+, which is effective on domian generalization recommendation.

- We conduct experiments on several datasets to compare our model with baselines, and analyse the results. And we release our project on Github Page.

## 3 Dataset Overview

| Dataset       | #User   | #Item  | #Inter  | #Domain |
| ------------- | ------- | ------ | ------- | ------- |
| CloudTheme-10 | 61,856  | 23,604 | 99,113  | 10      |
| CloudTheme-20 | 107,439 | 44,097 | 172,119 | 20      |
| CloudTheme-50 | 234,444 | 89,386 | 378,641 | 50      |
| KuaiRec-8     | 6,971   | 3,984  | 113,288 | 8       |
| KuaiRec-16    | 7,151   | 8,465  | 189,221 | 16      |
| KuaiRec-all   | 7,166   | 8,809  | 216,784 | 20      |



## 4 Quick Start

### Step 1: Download the project

First of all, download our project `HIRL_project.zip` from [Github](https://github.com/anonymous-hirl/HIRL/project) and unzip the file. The file includes both codes and datasets.

### Step 2: Create the running environment

Create `Python 3.9` enviroment and install the packages that the project requires.
- numpy==1.23.5
- scikit_learn==1.2.0
- torch==1.13.0

You can install the packages with the following command.

```
    pip install -r requirements.txt
```

### Step 3: Run the project

Choose a dataset to run (e.g. kuairec_8) and a model (e.g. DNN) to run with the following command.

```
    python run.py DNN dataset/kuairec_8.pickle DNN_kuairec_8 hidden_dim1 16 hidden_dim2 16 batch_size 1024 lr 0.05 epoch 10 
```

You can also use `quick_start.py` to run the project conveniently.

```
    python quick_start.py
```

You can also change the hyper-parameters as you want. The necessary hyper-parameters for each model have been recorded in the `hyper_parameters.py`.

### Step 4: Check the performance

The performance will be saved in `result` dictionary. The first column is the running time. The second column is the name of models. The third to the fourth columns are metrices `NDCG@10, HR@10` in order.


## 5 Hyper-parameters search range

We tune hyper-parameters accordingly, and the common hyper-parameters are presented on the following table.

| Hyper-parameter     | Explanation | Range |
| ------------------- | ---------------------------------------------------- | ------------------- |
| embedding_dim   | dimension of profiles      | \{16, 32, 64, 128\}             |
| hidden_dim1     | dimension of hidden layer1 | \{16, 32, 64, 128\}             |
| hidden_dim2     | dimension of hidden layer2 | \{16, 32, 64, 128\}             |
| lr              | learning rate of model     | \{0.001, 0.01, 0.05, 0.1, 0.2\} |
| batch_size      | batch size of model        | \{64, 128, 256, 512, 1024\}     |

As different base models have different hyper-paramerters to tune, you can view the details in the corresponding model files.