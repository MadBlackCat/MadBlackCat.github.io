# Word2Vec

标签（空格分隔）： NLP WordEmbeddingg

---

## Introduction ##

**Two model variants:**

 - Skip-grams (SG)
 - Continuous Bag of Words (CBOW)

**Additional efficiency in training:**

 - Negative sampling
 - Hierarchical Softmax
 
## Distribution Similarity ##

通过word的context来表示这个word

通过这个词的同伴来指导这个词的意思

## Main Idea ##

1. We have a large corpus of text 
2. Every word is represented by a **One Hot** vector 
3. Go through the text, which has a center word *c* and context ("outside") words *o* 
4. Use the similarity of the word vectors for *c* and *o* to calculate the    probability of *o* given *c*
5. Maximize this probability

![Example windows and process for computing][1]

## Skip-Gram ##


  [1]: F:%5CDocuments%5Cdocuments%5Cimg%5Cp1.png