---
title: DeepMutation Mutation Testing of Deep Learning Systems
tags: Paper

---


## Introduction

#### What problem does the paper solve

They solved the Testing Problem in Deep Learning. They **first** proposed a source-level mutation testing technique that works on training data and training programs.  

#### Why is the problem important

Today, deep learning is becoming more and more popular. Deep learning techniques are used in many areas, such as autonomous driving. However, with the witness of recent catastrophic accidents relevant to DL, the robustness and safety of DL systems become a big concern.Without a systematic way to evaluate and understand the quality of the test data, it is difficult to conclude that good performance on the test data indicates the robustness and generality of a DL system. So they used Mutation Testing to solve the problem.

#### Contribution

They proposed a mutation testing framework and workflow specialized for DL systems and designed eight source-level mutation operators and eight model–level mutation operator. They proposed two DL-specific mutation testing metrics and evaluated the proposed mutation testing framework on widely studied DL data sets and models.

## Background

#### Mutation Testing

Given an original program P, a set of faulty programs P' (mutants) are created based on predefined rules (mutation operators), each of which slightly modifies P. Specifically, the complete test set T is executed against P and only the passed tests T' are used for mutation testing. In the next step, each mutant of P' is executed on T'. If the test result for a mutant p' ∈ P' is different from that of P,  then p' is killed.  Then they could further enhance the quality of test set. 

**Mutation Score** is calculated as the ratio of killed mutants to all the generated mutants (i.e., #mutantskilled/#mutantsall ), which indicates the quality of test set.

#### Deep Learning System Development

**The Deep Learning System workflow:**  The developer collect data and write the Deep Learning Code. Finally train the data on program to general a model. So the most important things during the Deep Learning System model as follows:

- Training Data & Test Data
- Training Program
- Model

So they designed mutation operators focused on these.

## Source-level Mutation Testing of DL Systems

#### Workflow

At the initialization phase, a DL developer prepares a training program P and a set of training data D. After the training process, which runs P with D, a DL model M is obtained. When the mutation testing starts, the original training data D and program P are slightly modified by applying mutation operators, and the corresponding mutants D' and P' are generated. In the next step, either a training data mutant or training program mutant participates in the training process to generate a mutated DL model M'. When mutated DL models are obtained, they are executed and analyzed against the filtered test set T' for evaluating the quality of test data. 

![1560094491966](../../../assets/DM1.png)

#### Data Mutation Operators

| Fault Type           | Operation Description                                        |
| -------------------- | ------------------------------------------------------------ |
| Data Repetition (DR) | Duplicates training data<br />Duplicates specific type of data |
| Label Error (LE)     | Falsify results (e.g., labels) of data<br />Falsify specific results of data |
| Data Missing (DM)    | Remove selected data<br />Remove specific types of data      |
| Data Shuffle (DF)    | Add noise to training data<br />Add noise to specific type of data |




#### Program Mutation Operators

| Fault Type           | Operation Description                                        |
| -------------------- | ------------------------------------------------------------ |
| Layer Removal (LR)   | Remove a layer |
| Layer Addition (LAs) | Add a layer |
| Act. Fun. Remov. (AFRs)    | Remove activation functions      |


## Model-Level Mutation Testing of DL Systems

#### Workflow

![1560095370734](../../../assets/DM2.png)

Model level mutation testing directly changes the DL model M obtained through training from D and P. For each generated DL mutant model m' ∈ M' by our defined model-level mutation operators, input test dataset T is run on M to filter out all incorrect data and the passed data are sent to run each m'.

#### Model-level Mutation Operators

| Mutation Operator               | Description                               |
| ------------------------------- | ----------------------------------------- |
| Gaussian Fuzzing (GF)           | Fuzz weight by Gaussian Distribution      |
| Weight Shuffling (WS)           | Shuffle selected weights                  |
| Neuron Effect Block. (NEB)      | Block a neuron effect on following layers |
| Neuron Activation Inverse (NAI) | Invert the activation status of a neuron  |
| Neuron Switch (NS)              | Switch two neurons of the same layer      |
| Layer Deactivation (LD)         | Deactivate the effects of a layer         |
| Layer Addition (LA~m~)          | Add a layer in neuron network             |
| Act. Fun. Remov. (AFR~m~)       | Remove activation functions               |



## Evaluation

#### Mutation Testing Metrics

#### Subject Dataset and DL Models

#### Mutation Testing Evaluation and Results

#### Mutation Testing of Original Test Data by Class





## Compare to existing approaches

## Limitation

- The dataset in this paper only used MNIST and CIFAR-10, so we don't know how the result on other datasets. 
- The TensorFlow framework by default uses multiple threads for training procedure, which can cause the same training dataset to generate different DL models.
- The randomness during data sampling.

## Future Work

In future work, they will perform a more comprehensive study to propose advanced mutation operators to cover more diverse aspects of DL systems and investigate the relations of the mutation operators, as well as how well such mutation operators introduce faults comparable to human faults. Serial testing, attack and defense, as well as repair technique s for DL systems.

## What we learned

Every time we use deep learning, we can use the Mutation Testing mentioned in this paper to evaluate the quality of our test data after training our data. We can also observe the results of Mutation Testing and improve our test set. It can also be used as a measure of the robustness of our model.