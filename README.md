# FaceNet - A Unified Embedding for Face Recognition and Clustering

## Problem Statement

Despite significant recent advances in the field of face recognition, implementing face verification and recognition efficiently at scale presents serious challenges to current approaches.

## Solution Approach

-   A system is described which converts an image to a fixed size
embedding.
-   Distances between any two embeddings is a measure of the
similarity of the faces.
-   The embedding is produced by training a siamese network with
triplet loss.

## About Facenet

-   A unified system for face verification (is this the same person), recognition (who is this person) and clustering (find common people among these faces).
-   The embedding generated is an Euclidean embedding per image using a deep convolutional network.
-   The network is trained such that the squared L2 distances in the embedding space directly correspond to face similarity.
-   Faces of the same person have small distances and faces of distinct people have large distances.
-   Face verification simply involves thresholding the distance between the two embeddings, recognition becomes a k-NN classification problem; and clustering can be achieved using off-the-shelf techniques such as k-means or agglomerative clustering.
- Dataset to be used for training:- Labeled Faces in the Wild (LFW).

## Siamese Networks

-   Siamese Networks are basically two same neural networks, the output of which are passed through the a function that calculates the distance between the inputs.
-   For inputs belonging to same class, the outputs are close (i.e., distance is less) and for inputs belonging to different classes, the distance between outputs should be large.
-   Triplet loss can be used to train a siamese network.

![image](https://github.com/sanyamjain335/Facenet/blob/master/images/siamese.png?raw=true)

## Triplet loss

-   It is a distance based loss function that operates on three inputs:
    1. anchor (a) : is any arbitrary data point,
    2. positive (p) : which is the same class as the anchor
    3. and negative (n) : which is a different class from the anchor
-   Mathematically, it is defined as: L=max(d(a,p)−d(a,n)+margin,0).
-   We minimize this loss, which pushes d(a,p) to 0 and d(a,n) to be greater than d(a,p)+margin.
-   After the training, the positive examples will be closer to the anchor while the negative examples will be farther from it.

![image](https://github.com/sanyamjain335/Facenet/blob/master/images/TL.png?raw=true)

#### Triplet Loss function - 

![image](https://github.com/sanyamjain335/Facenet/blob/master/images/TL_loss_func.png?raw=true)

## Model Summary

![image](https://github.com/sanyamjain335/Facenet/blob/master/images/Model_summary.png?raw=true)

## Results

### Epoch vs Loss

![image](https://github.com/sanyamjain335/Facenet/blob/master/images/epochvsacc.png?raw=true)

### Scatter Plot for validation data and clusters

![image](https://github.com/sanyamjain335/Facenet/blob/master/images/scatter_plot.png?raw=true)

### Final best result

![image](https://github.com/sanyamjain335/Facenet/blob/master/images/final_result.png?raw=true)



