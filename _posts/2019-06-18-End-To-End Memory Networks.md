---
title: End-To-End Memory Networks
tags: Paper

---


## Introduction

Present a novel recurrent neural network (RNN) architecture where the recurrence reads from a possibly large external memory multiple times before outputting a symbol.

## Approach

![](../../../../assets/mnn.png)

### Single Layer

As (a):

##### Input memory representation

$$
p_{i}=\operatorname{Softmax}\left(u^{T} m_{i}\right)
$$

- $x_{i}$, sentence ( Bag of Words or other ...)
- $m_{i}$, the embedded vector of $x_{i}$ used embedding matrix $A$
- $q$, query (question) vector
- $u$, the embedded vector of $q$ used embedding matrix $B$

##### Output memory representation

$$
o=\sum_{i} p_{i} c_{i}
$$

- - $c_{i}$, the embedded vector of $x_{i}$ used embedding matrix $C$

##### Generating the final prediction

$$
\hat{a}=\operatorname{Softmax}(W(o+u))
$$

##### Loss Function

$$ cross-entropy(a, \hat{a}) $$

## Multiple Layers

As (b):
![](../../../../assets/mnnml.png)
$$
u^{k+1}=u^{k}+o^{k}
$$

$$
\hat{a}=\operatorname{Softmax}\left(W u^{K+1}\right)
$$

##### Two types of weight tying:
1. **Adjacent**
$$
A^{k+1}=C^{k}
$$
$$
W^{T}=C^{K}
$$
$$
B=A^{1}
$$
2. **Layer-wise (RNN-like)**
Comepare to RNN: (1) $u$, hidden state. (2) $p$, attention weights.
$$
A^{1}=A^{2}=\ldots=A^{K}
$$
$$
C^{1}=C^{2}=\ldots=C^{K}
$$
$$
u^{k+1}=H u^{k}+o^{k}
$$

## QA Experiment

##### Dataset: Synthetic QA tasks

![](../../../../assets/qa.png)

#### Sentence Representation
Two method:
1. bag-of-words (BoW)
2. embeds each word and sums the resulting vectors:$m_{i}=\sum_{j} A x_{i j}$, $c_{i}=\sum_{j} C x_{i j}$, $u=\sum_{j} B q_{j}$.

#### Position Encoding (PE),
$$
m_{i}=\sum_{j} l_{j} \cdot A x_{i j}
$$
$$
l_{k j}=(1-j / J)-(k / d)(1-2 j / J)
$$
The vector have information that the order of words.

#### Temporal Encoding ??
$m_{i}=\sum_{j} A x_{i j}+T_{A}(i)$, $c_{i}=\sum_{j} C x_{i j}+T_{C}(i)$
- $T_{A}(i)$ is the $i$th row of a special matrix $T_{A}$ that encodes temporal information.

#### Learning time invariance by injecting random noise ??

Randomly add 10% of empty memories to the stories.

#### Baselines

- MemNN
- MemNN-WSH
- LSTM

#### Results
![](../../../../assets/mnnex.png)
![](../../../../assets/mnnresult.png)
![](../../../../assets/mnncl.png)
## Language Model
![](../../../../assets/mnnperp.png)

- On language modeling tasks, it slightly outperforms tuned RNNs and LSTMs of comparable complexity
