# FastTextRank
## 简介
从中文文本中提取摘要和关键词<br/>
优化了算法收敛时间，和textrank4zh相比，速度提升了8倍<br/>
可以自由选择载入词向量字典，提高了准确性，但是载入词向量会使速度变慢
## 安装 
依赖：'Numpy>=1.14.5','gensim>=3.5.0'<br/>
pip install FastTextRank
# FastTextRank
Extract abstracts and keywords from Chinese text, use *optimized iterative algorithms* to improve running **speed**, and *selectively use word vectors* to improve **accuracy**.
## PageRank
PageRank is a website page ranking algorithm from Google.<br/>
PageRank was originally used to calculate the importance of web pages. The entire www can be seen as a directed graph, and the node is a web page.<br/>
This algorithm can caculate all node's importance by their connections.<br/>
* My algorithm changed the iterative algorithm to make the algorithm much faster, it costs 10ms per article, on the mean while TextRank4ZH costs 80ms on my data.<br/>
* My algorithm also use word2vec to make the abstract more accurate, but it will cost more time to run the algorithm. Using word2vec costs 40ms per article on the same traning data.

## W2VTextRank4Sentence
### Introduction
1. Cut article into sentence
2. Calculate similarity between sentences:
   * Using word vectors' cosine similarity
   * Using two sentences' common words
3. Build a graph by sentences' similarity
4. Caculate the importance of each sentence by improved iterative algorithm
5. Get the abstract
### API
* use_stopword: boolean, default True
* stop_words_file: str, default None.
The stop words file you want to use. If it is None, you will use this package's stop words.
* use_w2v: boolean, default False
If it is True, you must input passing dict_path parameter.
* dict_path: str, default None.
* max_iter:maximum iteration round
* tol: maximum tolerance error

## W2VTextRank4Word

### Introduction
1. Cut artile into word
2. Calculate similarity between word: 
   If two words are all in window distance, then the graph's side of this two word add 1.0. Window is set by user.
3. Build a graph by word' similarity
4. Caculate the importance of each word by improved iterative algorithm
5. Get the key word

### API
* use_stopword=boolean, default True
* stop_words_file=str, default None.
The stop words file you want to use. If it is None, you will use this package's stop words.
* max_iter=maximum iteration round
* tol=maximum tolerance error
* window=int, default 2
The window to determine if two words are related
 
