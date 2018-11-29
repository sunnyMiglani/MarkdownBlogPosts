# N-Grams and Bag of Words

N-Gram is a contiguous sequence of n words:
    - " Dog that barks does not bite"
    - Unigram: Dog, that, barks, does, not, bite.
    - BiGram: Dog that, that barks, barks does, does not, not bite...
    
Bag-of-Words: Method of representing the data using n-grams, usually unigrams.
  **It does not keep track of the order of the text**
  

# Representations of Text:

- One-Hot Encoding:
    Each vector corresponds to a unique word in the corpus. The vector is of length of corpus, and marks 1 where the word is present, 0 elsewhere. It's a **good input to functions that requre a paritcular input range, for example neural nets**
- N-Gram Models:
    N Sequence of tokens into account. Ususally part of another implementation, not much use alone.
- Word2Vec:
    Algorithm that comprises of 2 models, **continous bag of words** or **skip-gram**. The embeddings are created via a **two-layer neural network**, where the model corresponds to a prediction task.
    
    For **CBOW**: Objective is predict a word given some context (autocomplete). 
    For **Skip-Gram**: Predict the context of the given word. 

    The final output of the model is used only for training reaons, because we ignore the output vector and only look at the weights in the hidden layer, which is used as the vector representation for the texts.
    
    
### Explanation for CBOW and Skip-Gram

- Classic Word2Vec: 
It uses a single hidden layer, fully connected neural network. 
The neurons in the hidden layer are all linerar neurons, and the input layer is as big as the vocabulary of the training set.
The hidden layer is set to the dimensionality of the resulting word vectors. The output size is same as the input size.
The input to the hidden layer can be represented by size V x N (v = num of words, N dimension of word vectors). The output of the hidden layer is represented by NxV. 
Where N is the number of neurons in the hidden layer (it matches the dimensionality of the word vector needed). 
Word2Vec creates a vector by **converting the activation values of the ouput layer neurons to probabilities using the softmax function**. 


- Continous Bag of Words Model:
Similar to the Word2Vec, but we'd feed in multiple words, (n) as the input, and the output would be the associated expected word. This way we can train the net to expect n inputs and provide a valid output that's the expected word. 
n words represent context, and the output is known as the target word.

- Skip-Gram Model: 
The model reverse the use of target and context word. The target word is fed as the input, and the context is the expected output. 
It would produce n vectors for each input word, which means you'd expect multiple layers of output, that are sized N(dimension of vector). 

# GloVe: Word Embedding

### word2vec problems
Let's start by summarizing word2vec: This trains word embeddings by optimising a loss funciton with gradient descent (classic NN), the loss function is computed **by measuring how well a certain word can predict it's surrounding words**. word2vec **only takes local contexts into account!**. We need to take global count statistics into consideration in sentences.

word2Vec has/had the advantage over prexisting vector/matrix representations due to the simple vector arithmetic that could be done over the values of the vectors created.
For example

> king - man + woman = queen

Was valid maths in the values generated by the word2vec system. (**Called Dimensions of Meaning**).

**GloVe wanted to take both the dimensions of meaning and the global information into consideration**


## GloVe "Step By Step"

First step of GloVe is to remove the need to stream the sentences, by creating a co-occurance matrix. Specifically using a fixed window size, looking at the number of times a number is seen. This leads to a symmetric matrix as the presence of A indicates B and this applies vice versa as well.

Now we look at how these statistics of co-occurance affect the words themselves. We understand the principle that **co-occurance ratios between 2 words in a context are strongly connected to each other**
Example given in [the paper blog i'm using to understand this](http://mlexplained.com/2018/04/29/paper-dissected-glove-global-vectors-for-word-representation-explained/) is that you can expect "ice" and "steam" to be related, and "ice" to be more often seen with "solid" than "gas"and neither to be seen related very much to "fashion".






# Text Classification Pipeline:

1. Training Text: Input text which is used for learning to predict the classes
2. Feature Vector: A vector that has information describing the characteristics of the input data
3. Labels: Categories or lables our model should predict
4. ML Algorithm: The algorithm (maths) being used to learn over the data, in our case it's CNN.
5. Predictive model: The model we create taht can perform label predictions


    
