# User Profile Preserving Social Network Embedding (UPPSNE)

Code for IJCAI-2017 paper "User Profile Preserving Social Network Embedding"

Authors: Daokun Zhang, Jie Yin, Xingquan Zhu and Chengqi Zhang

Contact: Daokun Zhang (daokunzhang2015@gmail.com)

This is the updated implenmentation. Different from the original version trained by gradient descent, this version is trained by stochastic gradient descent, which is more effient.

The model is trained as follows:

1. Generate a stream of short random walk sequences on the given network.

2. Count the occurrence frequencies for all node context pairs within a window size on the generated random walk sequences.

3. Accorind to the occurrence frequecies, randomly select a node context pair and update the corresponding gradients.

4. Repeat step 3 until a pre-defined number of iterations elapsed.

Please run the "UPPSNE.sh" file to run this implementation on the Facebook network.

The format of the input network is as following:

In the input file, the first line is the number of nodes ("node_num") and the number of node content attributes ("feat_num") seprated by whitespace:

    node_num feat_num

From the second line, one by one, each user's id, neighbor list and profile features are provided. The following is the information for a node:

    node_id
    neigh_num
    neigh_id1 neigh_id2 neigh_id3 ......
    nonzero_feat_num
    nonzero_attribute_id1 nonzero_attribute_val1 nonzero_attribute_id2 nonzero_attribute_val2 ......

Above, "node_id" is the id of current node. "neigh_num" is the number of neighbors of current node, and "neigh_id1, neigh_id2, neigh_id3..." is the neighbor list of current node. "nonzero_feat_num" is the number of observed nonzero feature values of the current node and "nonzero_attribute_id1 nonzero_attribute_val1 nonzero_attribute_id2 nonzero_attribute_val2 ......" is the nonzero feature value list of current node, where "nonzero_attribute_id1" is the id of the observed attribute in which current node take nonzero value and "nonzero_attribute_val1" is the corresponding attribute value.

Taking the "Facebook.graph.txt" as an example, its input is:

    3232 1403
    0
    5
    18 20 25 34 46
    7
    1 1 578 1 664 1 780 1 927 1 1166 1 1344 1
    1
    0
    2
    663 1 927 1
    2
    0
    3
    324 1 663 1 927 1
    3
    0
    4
    328 1 663 1 927 1 1344 1
    4
    0
    9
    167 1 168 1 363 1 396 1 574 1 581 1 582 1 663 1 927 1
    5
    1
    9
    8
    83 1 664 1 817 1 927 1 953 1 1166 1 1170 1 1348 1
    ......

The options of UPPSNE are as follows:

    -graph <file>
		The input <file> for network embedding
	-output <file>
		Use <file> to save the resulting network embeddings
	-time <file>
		Use <file> to save running time
	-size <int>
		Set size of learned dimensions; default is 128
	-window <int>
		Window size for collecting node context pairs; default is 10
	-walknum <int>
		The number of random walks starting from per node; default is 40
	-walklen <int>
		The length of random walks; default is 100
	-negative <int>
		Number of negative examples; default is 5, common values are 3 - 10
	-alpha <float>
		Set the starting learning rate; default is 0.025
	-samples <int>
		Set the number of training samples as <int> Million; default is 100

If you find this project is useful, please cite this paper:

	@inproceedings{zhanga2017user,
  	    title={User profile preserving social network embedding},
  	    author={Zhang, Daokun and Yin, Jie and Zhu, Xingquan and Zhang, Chengqi},
  	    booktitle={IJCAI},
  	    pages={3378--3384},
  	    year={2017}
	}


