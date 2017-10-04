# Encoding the AST Tree using a strategy similar to word2vec, but applied to the context of AST's

This works is an attempt to learn vector representation for AST nodes. The original paper is: https://arxiv.org/abs/1409.3358. Since this paper is difficult to implement, I applied the strategy similar to word2vec to learned embeddings of AST nodes. 

* Vectors are learned by a variation of word2vec instead of the proposed method. The intuition is similar to the original paper, capture the context of a parent node by learning the vectors of its children. The difference is that in the original paper, they tried to minimizing the distance between the parent node and the sum vectors of it children. In this work, given a specific token type as the input, look at its children and pick one at random. The network is going to tell us the probability for every token in our vocabulary of being its child that we chose. The vocabulary is relatively small since the number of token type of AST is small (around 92 token type).

* Adam is used instead of gradient descent.

* The dataset used in this implementation is smaller than in the original paper. I crawled Python algorithms from Github by myself since using the built in Python AST parser for Python code is more convenient and less time-consuming than writing the AST Parser for the C++ code in the original dataset, thus the node type is a little bit different.

The list of learned token vectors can be found here:
https://github.com/bdqnghi/ast-node-encoding/blob/master/data/vectors.txt

A visualization of learned token
--------------------------
![](ast_nodes_visualization.png)
