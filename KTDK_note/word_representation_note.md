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
* But this can be solved using the RNN which will take one word to feed the NN for each step rather than sweeping the whole phrase at the same time. 
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/Jxuhl/sentiment-classification).

> Machine translation, sequence to sequence!
* RNN for encoder ( input ), RNN for decoder ( output) 
> Image Captioning, convolution to sequence!
* CNN for image ( input ) , reomve the softmax from the common CNN but input the CNN output to the RNN where we will get the corresponding caption ( output)
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/HyEui/basic-models).

> We do not use greedy search algorithm in machine translation because it picks up the best probabiltiy of one word at a time, resulting in poor translation. Therefore, Beam Search, conditional language model, that gives the maximum probabiity of the whole sentence, must be used.
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/v2pRn/picking-the-most-likely-sentence).

### Beam Search
* Let's see how the process goes for French to English translation.
> Step 1: 
>
> Put the sentence (French) into the encoder. 
> Decoder : Pick the first most likely words from the English vocabulary ( the number of most likely words can be decided by the Beam Width).
>
> Step 2:
>
> The second most likely words can be decided from the first most likely word. 
> This is denoted as P( y2 | x, y1 )
> However, we are interested in the probability of the most likely pair for both y1 and y2; not only y2). 
> To get this, you can use the following formula. 
* P( y1, y2 | x ) = P( y1|x ) * P( y2| x, y1 )
>
> It keeps on going in this way.
* Remember!!! 
> if beam_width = 1;
>     algorithm = greedy_search_algorithm

> Here we try to maximize P (  y1, y2, ....., y(n) | x ) 
* However, this is the multiplication of probabilities in which each probability is less than one, resulting in a tiny output. Hence, we'll get the short translation which is more likely to get wrong. 
> To solove this, we use log !
> However, there is also the case producing very large output!
> So we need to average the output!
> Divide the log(Probaility) by the lenght of the phrase!
* Here we can also a soft approach. Use exponent on the length! But don't set the exponent 0 or 1! You know the reason!
> For more details, [check this out](https://www.coursera.org/learn/nlp-sequence-models/lecture/AkjG2/refinements-to-beam-search).

### Beam Search is an approximate search algorithm. It is a heuristic search algorithm.
#### It doesn't provide you the exact output like the Depth Frist Search or Breadht First Search does. 
