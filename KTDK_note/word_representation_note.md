# Warning!

### this is just my scratch note, not well-prepared document !!!!

## I just aim to use this note for my personal review later on. 

### It may not be helpful to you cos it is not well-planned and organized one.

> Let's go from one-hot representation to featurized representation!!! This is also known as the word embedding.
For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/6Oq70/word-representation).

> Smaller datasets with word embedding can be used together with Transfer Learning( Learned from the larger corpus that will be appiled to the smaller dataset ). 
For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/qHMK5/using-word-embeddings).

> Word embedding is useful for analogy reasoning. 
- Man ----> Woman
- King ---> ?
* embedding(Man) - embedding(Woman) = embedding(King) -embedding(?)
> Let's denote e as embedding.
> Cosine Similarity
* sim( e(?), e(King) - e(Man) + e(Woman) ) 
* = sim ( e(w), e(King) - e(Man) + e(Woman) )
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/S2mat/properties-of-word-embeddings).

> Embedding algorithm is learning about embedding matrix. 
* To get e(j),
*   Featurized_Vector(i, j)  * One_hot_Encoding( j, k) = embedding(i, k) = e(i,k)
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/K604Z/embedding-matrix).

> It is common to use the last word to predict the target word.
* Here the problem is
> ### How do we choose the context word?
> #### We can opt for the context word randomly with the avoidance of some frequent words such as 'the', 'a', 'an' and so forth. 
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/APM5s/learning-word-embeddings).

> We can make the above lateset mentioned way easier with the help of " #### Negative Sampling" algorithm which retrieves negative k target words with postive 1 target word for each epoch. Hence, the computation cost will be greatly reduced. 
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/Iwx0e/negative-sampling).

> In GloVe algorithm, you'll see frequent words like "the" and so forth with more weight, uncommon word such as "durian" with a little weight.
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/IxDTG/glove-word-vectors).

> Sentiment analysis is telling likes/dilikes from the a piece of text. You don't have much training labels for this process but you can rely on word embeddings.
* Firstly, take one-hot vector for each word, 
* and multiply it with the embedding matrix which comes from the word embeddings(featurized map, if I am not mistaken, with some axes, which shows the degree of the word in each axis) , then 
* we'll get the knowledge of the corresponding word( which word is frequent and useless and which word is neceesary for the later on process).
* then, average or sum the output and pass it to softmax classifier.
*however,this approach has a negative impact and produces biased outcomes due to the lack of the word order.
* But this can be solved using the RNN which will take one word to feed in the NN for each step rather than sweeping the whole phrase at the same time. 
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/Jxuhl/sentiment-classification).
