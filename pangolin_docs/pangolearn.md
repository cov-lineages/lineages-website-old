---
layout: page
title: pangoLEARN
---


### PANGOLIN 2.0

This release of pangolin comes with some major changes, including a significant speed-up and improvements in assignment accuracy for larger lineages.  The new assignment algorithm (that we have termed pangoLEARN) is described in detail below.

One significant benefit of this approach over the previous algorithm is that it allows us to incorporate all of the diversity of the large lineages into the assignment system rather than just picking a few representative sequences.

We have pulled out informative sites and this information is included in the data release on <a href="https://github.com/cov-lineages/pangoLEARN/tree/master/pangoLEARN/supporting_information">pangoLEARN</a>. The top SNPs that are  most positively and negatively associated with a given lineage are detailed in those files. More details on this release and its practicalities can be found  <a href="https://github.com/cov-lineages/pangolin/releases/tag/v2.0">here</a>.</p>

pangoLEARN is an alternative algorithm for lineage assignment, which uses machine learning, implemented as of pangolin 2.0. This new algorithm, which relies on machine learning, offers much faster lineage assignment, as the phylogenetic approach was struggling to scale with the increase in number of lineages needing to be represented in the guide tree. This new approach also takes into account all of the diversity present within a lineage rather than just selecting a representative few. The consequences of this approach mean that for large lineages, we have improved our recall and precision significantly. We are continuing to develop more sophisticated approaches to machine learning for lineage assignment, which we hope will offer even better improvements in both speed and accuracy.

<section>
  <div class="row">
    <h3>pangoLEARN description</h3>
        <p>The current version of <strong>pangoLEARN</strong> uses a classification tree, but the pipeline has been written so that as more complex models are developed,the user will be able to choose which model to use to assign their lineages. The previous version of <strong>pangoLEARN</strong>  used multinomial logisitc regression, which is still available for download at the previous tagged release on GitHub.</p>
        <p>The model was trained using ~60,000 SARS-CoV-2 sequences from GISAID, acknowledgements <a href="./gisaid_acknowledgements.html">here</a>, with their lineages assigned by manually curating the global ML tree, as is the standard lineages data release procedure for <strong>pangolin</strong>. Each base of each genome was <a href="https://www.hackernoon.com/what-is-one-hot-encoding-why-and-when-do-you-have-to-use-it-e3c6186d008f">one-hot</a> encoded. This left us with a large number of parameters to train, which is why training this model takes approximately 30 minutes on our hardware (may change with different hardware). This model was built using the standard <a href="https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html">sci-kit learn implementation</a> of a decision tree learning algorithm. The code for this process is available in the <a href="https://github.com/cov-lineages/cov-support/blob/master/cov_support/scripts">cov-lineages/cov-support</a> repository.</p>
    </div>
    <div class="image object">
    <span class="image object">
        <img src="./assets/images/pangolearn.png" alt="" style="max-height:460px;max-width:500px"/>
    </span>
</div>
</section>
<section>
  <div class="row">
    <div class="6u 12u$(small)">
        <h3>Multinomial logistic regression</h3>
        <p>While in standard regression a line of best fit is found for a set of training data, which represents a linear relationship between variables of interest, a logistic regression fits a <a href="https://en.wikipedia.org/wiki/Sigmoid_function">sigmoid function</a> to the training data, in order to tell two different classes apart. A multinomial logistic regression is an extension of a standard logistic regression in that it can be used to classify more than two classes. Each potential assignment (i.e. lineage) is modeled as a set of n-1 independent binary choices (sigmoid functions), where n is the number of classes.</p>
        <p> Multinomial logistic regression is an extremely commonly used model as it is able to simply and intuitively assign probabilities to class assignments. However, it does not incorporate any hierarchical structure. We are currently developing new models that do incorporate hierarchical structure. However, given the limitations of this simple model, it has performed surprisingly well with this data. While more complex models may offer improvements in assignment accuracies for smaller lineages, the logistic regression has the advantages of being intuitive, easy to implement, and relatively fast to train.</p>
    </div>
    <div class="6u$ 12u$(small)">
        <h3>Decision Trees</h3>
        <p>Decision trees are especially intuitive models. A series of if-then-else decision rules are learned from the input data and assembled into a hierarchical structure. The internal nodes represent a decision between a number of paths, and the leaf nodes represent a final classification. By learning this tree structure from data which itself comes from a phylogenic tree, we are representing this underlying phylogenic tree structure in a way which can be more easily harnessed for sequence classification.
        </p>
        <p>Decision trees can sometimes be thought of as brittle as small changes in the training data can potentially result in large changes in the tree structure. However, several similar model types were tested in preparation for this data release, including various Random Forest models, which are generally thought to be more robust than decision trees. The simpler decision tree performed the best both in terms of accuracy and training time. Because the older pieces of the underlying phylogenic tree structure will remain stable, this seems to be a case where the normal stability concerns associated with this model are less relevant.</p>
    </div>
  </div>
</section>


### [Next: Dependencies](./requirements.html)