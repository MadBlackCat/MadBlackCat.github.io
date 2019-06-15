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
It proposed two kinds of mutation testing metrics for DL Systems in this paper. They are MutationScore and AveErrorRate, respectively. Suppose we have a k-classification problem and let C = C = {c1 , . . . , ck} be all the k classes of input data. For a test data point t’ ∈ T’, we say that t’ kills ci ∈ C of mutant m’ ∈ M’ if the following conditions are satisfied:
1. t’ is correctly classified as ci by the original DL model M

2. t’ is not classified as ci by m’.

They define the mutation score for DL systems as follows, where KilledClasses(T’,m’) is the set of classes of m’ killed by test data in T’:

$$
\left(T^{\prime}, M^{\prime}\right)=\frac{\sum_{m^{\prime} \in M^{\prime}} | \text { Killed Classes }\left(T^{\prime}, m^{\prime}\right) |}{\left|M^{\prime}\right| \times|C|}
$$

They define average error rate (AER) of T’ on each mutant model m’ ∈ M’ to measure the overall behavior differential effects introduced by all mutation operators.

$$
\left(T^{\prime}, M^{\prime}\right)=\frac{\sum_{m^{\prime} \in M^{\prime}} \text { ErrorRate }\left(T^{\prime}, m^{\prime}\right)}{\left|M^{\prime}\right|}
$$

#### Subject Dataset and DL Models

It selected two popular publicly available datasets MNIST (digits from 0 to 9) and CIFAR-10 (e.g., airplanes, cars, birds, and cats) as the evaluation subjects. each of it has 10 classes. Then it sampled 5, 000 data from original training data while setting two sampled 1, 000 from the accompanied test data. To demonstrate the usefulness of the mutation testing for the measurement of test data quality, it performed a controlled experiment on two data settings (see figure 3). Each setting has a pair of dataset(T1, T2), where T1 is uniformly sampled from all classes Which means the first group covers more diverse use-case of the DL software of each class and T2 is non-uniformly sampled which means the second group mainly focuses on a single class. In order to avoid randomness, it repeats the data sampling for each setting five times (i.e., and averages the mutation testing analysis results. The studied DL models A, B, and C contain 107, 786, 694, 402, and 1, 147, 978 trainable parameters, respectively. To generate model-level mutants at the weight and neuron level, it configures to sample 1%, weights and neurons from the studied DNNs, and use the corresponding mutation operators to randomly mutate the selected targets.

![1560592876499](../../../assets/1560592876499.png)


#### Mutation Testing Evaluation and Results

After the controlled datasets and mutant models are generated, the mutation testing starts the execution phase by running candidate test dataset on mutant models, after which it calculates the mutation score and average error rate (AER) for each dataset and the following results can be gotten.

![1560593053780](../../../assets/1560593053780.png)

As figure, most of the AERs are relatively small, and for source-level mutation testing of model B, the obtained AER of 1, 000 uniformly sampled test data (i.e., 0.66%) is higher than the one obtained from the uniformly sampled 5, 000 training data (i.e., 0.49%). This is more obvious on model C. When the same sampling method is used, the AER obtained from the sampled 1000 test data is all higher than the sampled 5, 000 training data. The same conclusion could also be reached by observing the mutation score (see Figure 5(a) and (b)). The mutation scores on model A and B are the cases where a larger data size obtains a higher mutation score, whereas the result on model C shows the opposite case. When performed on the same set of data, the source-level mutation testing and model-level mutation testing show some different behaviors. For example, comparing the same data pair setting of Figures 5(a) and 6(a), the source-level mutation testing obtains lower mutation score on model A, but obtains higher mutation score on model B. This means that the same 1% mutation ratio results in different DL mutant model effects by source-level and model-level mutation testing procedure. In both Figure 5 and 6, we observe that the mutation scores are still low for many cases. It indicates that corresponding evaluated tests are low-quality, which is understandable in high-dimensional space.

#### Mutation Testing of Original Test Data by Class

![1560593265825](../../../../assets/1560593265825.png)

 

![1560593279921](../../../assets/1560593279921.png)

![1560593288482](../../../assets/1560593288482.png)

- Test Data and Mutant Models : Similar to the experimental procedure in Section 5.2, we first prepare the test data of each class for mutation testing. For the accompanied original test data in MNIST (CIFAR-10), we separate them into the corresponding 10 test dataset by class (i.e., t1, t2, . . . , t10). For each class of the test data ti, we follow the same mutation testing procedure to perform data filtering procedure on model A, B and C, respectively. In the end, we obtain 30 test datasets, including 10 datasets by class (i.e., t0 1, t0 2, . . . , t0 10) for each studied DL model.We reuse the generated model-level DL mutant models of Section 5.2 and perform mutation testing on the prepared dataset.
- Mutation Testing Results of Test Data by Class: Figure 7 summarizes the obtained mutation score and AER for each model. We can see that, in general, the test data of different classes obtain different mutation scores and AER. Consider the results of model A as an example, the test data of class 3 obtains the lowest mutation score and AER (i.e., 6.25% and 1.48%). It indicates that, compared with the test data of other classes, the test data of class 3 could still be further enhanced. In addition, this experiment demonstrates that a higher AER does not necessarily result in a higher mutation score. For model A, the AER obtained by class 1 is larger than class 2 while the mutation score of class 1 is smaller.



## Limitation

- The dataset in this paper only used MNIST and CIFAR-10, so we don't know how the result on other datasets.
- The TensorFlow framework by default uses multiple threads for training procedure, which can cause the same training dataset to generate different DL models.
- The randomness during data sampling.

## Future Work

In future work, they will perform a more comprehensive study to propose advanced mutation operators to cover more diverse aspects of DL systems and investigate the relations of the mutation operators, as well as how well such mutation operators introduce faults comparable to human faults. Serial testing, attack and defense, as well as repair technique s for DL systems.

## What we learned

Every time we use deep learning, we can use the Mutation Testing mentioned in this paper to evaluate the quality of our test data after training our data. We can also observe the results of Mutation Testing and improve our test set. It can also be used as a measure of the robustness of our model.
