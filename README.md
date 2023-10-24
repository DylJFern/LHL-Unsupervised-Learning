# Unsupervised Learning

## Project/Goals
The objective of this project was to use usupervised learning techniques to explore data containing information about various products sold by a grocery store and gain insights using different algorithms. 

## <br>Process
The project involved exploratory data analysis and pre-processing in which the imported ['wholesale.csv'](data/wholesale.csv) (obtained from [Kaggle](https://www.kaggle.com/datasets/binovi/wholesale-customers-data-set)) dataset was analyzed and visualizations were created to examine the relationships between the different variables, handle outliers and incorrect values, standardize the features by scaling the data and normalize using transforms, as well as performing feature engineering as needed.

With the preliminary steps completed, we could then perform analysis by grouping products together into clusters based on their attributes or data points using K-Means and Hierarchical Clustering. We could then compare the cluster performance through number of common points or visualizations for how each group the data. Finally, we could perform principal component analysis to draw conclusions about the underlying structure of the wholesale customer data, as well as gather insights as to how businesses can improve possible revenue by minimizing products of least importance based on customer purchasing data through dimensionality reduction.

## <br>Results
### EDA Process and Pre-processing
- In this stage, we noticed the data contained no null and duplicate values; however, it did contain outliers. But, based on the context, the outliers were meaningful. For example, the dataset represents the annual spending and for the category 'Fresh_log', the outliers (approximately less than 6) would simply mean there were situations with minimal levels of spending (which makes sense as this could depend on individual purchasing habits).
- The data contained categorical variables 'Channel' and 'Region' where we applied one-hot encoding as there did not exist any ordinal relationship between them. What this meant was, it would create these dummy variables (separate binary columns for each category), indicating the presence (1) or absence (0) of the category.
- All the data was then plotted in a correlation matrix to determine the relationships between the variables. For example, 'Grocery_log' and 'Detergents_Paper_log' had a correlation of 0.8, as such businesses could consider such a relationship when making stocking decisions.

### Clustering
- For K-Means, we selected the optimal number of clusters as 4 based on the graph and data obtained from the 'elbow' plot. Using this k = 4 clusters we were able to obtain the data points within each cluster as well as determine the number of iterations to achieve convergence was 8.
  - Cluster 1 was the largest, indicating the prevalence of a certain type of customer in the dataset, conversely, cluster 0 was the smallest, potentially representing a niche market segment.
- For Hierarchical Clustering, we constructed a dendrogram and from it we could determine the number of clusters through a variety of methods. For instance, one could choose a threshold distance at which to cut the dendrogram. In this case, the number of clusters was selected to be 4 such that a comparison to K-Means clustering could be made.
- Although we did not get to fully explore the comparison between the two clustering techniques (due to time limitations), we briefly compared the number of data points within each cluster and examined any common points (intersections) that existed. Overall, there was a lack of consistency between the two methods as indicated by the low number of common points.

### Principal Component Analysis (PCA)
- This type of feature engineering was skipped in the EDA and pre-processing stage, solely because it did not make sense for it to be conducted twice.
- Here, we first observed the Skree plot along with the explained variance of each component. By considering the cumulative explained variance, it was determined that the first 3 components could preserve approximately 72% of the total variance, able to capture a substantial portion of the data's variability.
  - This signifies that businesses can effectively reduce the data's dimensionality while retaining the core information (in other words, minimizing loss and maximizing revenue).
  - Based on this factor, we selected our number of PCA components as 3.
- Upon conducting a feature importance analysis we were able to observe that "Fresh_log", "Delicassen_log", and "Frozen_log" have the highest overall combined influence.
  - This indicates that these product categories are important drivers of customers' behaviour, as such the business should focus on understanding customer preferences and demends within these categories.

## <br>Challenges
- The time constraint limiting the feasibility of particular tasks.
- The decision on whether to one-hot encode the categorical variables or just drop them all together.
- Estimations and assumptions made based on number of clusters for clustering algorithms and number of components for PCA.

## <br>Future Considerations
- Include additional clustering algorithms as well as plotting the clusters along with their centroids to gain a visual representation of how the different techniques may vary.
- Implement random forest regression as part of the feature selection procedure in EDA and pre-processing.
- Explore further relationships with variables and incorporate other business insights not previously considered.
