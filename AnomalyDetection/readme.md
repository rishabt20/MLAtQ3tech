# Isolation Forest

Isolation Forest is an anomaly detection algorithm that isolates anomalies by randomly partitioning the data space. Here's how it works:

- In an Isolation Forest, randomly sub-sampled data is processed in a tree structure based on randomly selected features.
- The samples that travel deeper into the tree are less likely to be anomalies as they required more cuts to isolate them.
- Similarly, the samples which end up in shorter branches indicate anomalies as it was easier for the tree to separate them from other observations.

## Isolation Tree (iTree) Algorithm:

1. **Sub-sampling:** When given a dataset, a random sub-sample of the data is selected and assigned to a binary tree.
2. **Feature Randomization:** Branching of the tree starts by selecting a random feature (from the set of all N features) first. And then branching is done on a random threshold (any value in the range of minimum and maximum values of the selected feature).
3. **Binary Split:** If the value of a data point is less than the selected threshold, it goes to the left branch else to the right. And thus a node is split into left and right branches.
4. **Recursive Partitioning:** This process from step 2 is continued recursively till each data point is completely isolated or till max depth (if defined) is reached.

The above steps are repeated to construct random binary trees.

After an ensemble of iTrees (Isolation Forest) is created, model training is complete.

## Scoring:

During scoring, a data point is traversed through all the trees which were trained earlier.

Now, an ‘anomaly score’ is assigned to each of the data points based on the depth of the tree required to arrive at that point. This score is an aggregation of the depth obtained from each of the iTrees.

---

By employing this algorithm, Isolation Forest provides a robust solution for detecting anomalies efficiently.

