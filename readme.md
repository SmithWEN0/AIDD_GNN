# Summary

Previously, an ANN model was constructed to learn the fixed molecular representation and to predict pIC50 values for virtual screening. While the constructed ANN model showed good performance with an RMSE value of around 1.1 and an R square score of approximately 0.84 on the testing dataset, the overfitting issue was unsolved when the model was established on GitHub. Such a four-layer ANN model was so complex that it learnt the noise instead of representational features in this small raw dataset, which led to a much higher R2 score on training datasets than on testing datasets. The potential solutions to overcoming overfitting were implemented with little improvement, including adding a dropout layer and batch normalization layer. Although the 'early stop' technique had not been used before the establishment of this ANN model, it was still insufficient since the architecture of this model was complicated for the small CheMBL dataset.

However, GCN models could not only mitigate the overfitting problem but also increase model interpretability as well as model performance. They generally consist of two different components for extracting features from protein and ligand graphs respectively, as well as a fully connected predictor. Molecular graphs, for instance, can interpret atoms as nodes and chemical bonds as edges. Furthermore, the domain knowledge, such as the names of atoms and the types of chemical bonds, is added into the model as node or edge features. These representative approaches improve model interpretability. In addition to this, GCN models outperform the previous ANN model in terms of MAE value. Three models were constructed with the same hyperparameters based on three tested targets, achieving MAE values below 0.4 and R2 scores above 0.6 without overfitting. The statistics imply that the model made an accurate prediction but only a small proportion of variance can be explained by the model.

# Problem

## 1. Datasets

Across the three tests on different targets, the datasets were downloaded from the CheMBL and BindingDB websites. While these two datasets focus on various aspects of small molecules, they share many similarities. The null hypothesis was not rejected when t-test was performed the check their similarities. In other words, using the combined datasets may not contribute to dramatically increasing model performance. Therefore, more diverse datasets should be investigated, such as PDBbind. This database has become the benchmark in this field and contains multiple proteins as well as their corresponding ligand. However, each protein only has one corresponding ligand, which indicates the present procedure of data pre-processing requires modification.

## 2. Fixed Representation vs Learning Representation

When reading research papers, I found the difference between fixed representation and learning representation. The fixed representation approach includes Morgan fingerprints, which were used in the previous ANN and widely accepted in conventional machine learning models. One paper even mentioned that models using fixed representation, especially the SVM and RF, outperformed the ones using learning representation. Conversely, the phrase 'learning representation models' refers to the models capable of learning representational features themselves, such as GCN models. While most of the reported GCN models only achieved a comparable or moderate performance, their model interpretability and generalization ability excel the conventional machine learning models. Maybe the time is of great essence for proposing novel algorithms and improving the performance of GCN models, but the nature of these models is suitable for dealing with drug discovery problems.

# Next
Focus on the proposed two problems, and read research papers to find solutions.
1) Try PDBbind database
2) Try to combine both learning and fixed representation
