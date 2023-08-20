---
output:
  pdf_document: default
  html_document: default
---
# STA 380 -Intro to ML Part 2 - Assignment
## Group Members - Fangshu Song, Siyi Liu, Vishal Anand Gupta, Yu Xia


## Probability practice

The detailed calculation steps for both parts can be found in 
<a href="https://github.com/dongdanyu/ml_final_project/blob/main/probability_practice/Probability Practice.ipynb">Probability Practice</a>.

__Part A.__ 

The fraction of people who are truthful clickers and answered "Yes" is approximately 0.7143 or 71.43%.

__Part B.__ 

The probability that a person has the disease given they tested positive is 0.00989 or 0.989%.


## Wrangling the Billboard Top 100  

The code and visualizations for part A, B and C can be found in 
<a href="https://github.com/dongdanyu/ml_final_project/blob/main/wrangling_billboard_top_100/Wrangling the Billboard Top 100.ipynb">Wrangling the Billboard Top 100</a>.

__Part A__:

The table below captures the essence of the top 10 most popular songs since 1958, meticulously curated based on their enduring impact and the total number of weeks they graced the esteemed Billboard Top 100 chart. Comprising a blend of genres and artists, the table encapsulates the musical journey of these songs that have left an indelible mark on the cultural fabric.

![top_100_songs](/wrangling_billboard_top_100/Top_10_most_popular_songs_since_1958.png)


__Part B__: 

The line chart below illustrates the evolution of "Musical Diversity" from 1959 to 2020, as measured by the number of unique songs released in each specific year. The trend showcases distinct phases of change, marked by periods of decline, recovery, and remarkable resurgence.

![Musical_Diversity](/wrangling_billboard_top_100/Musical_Diversity.png)

Some insights on the trend:

- In the early years, from 1959 to the late 1960s, the musical landscape was characterized by a diverse array of songs, reflecting a dynamic and experimental era in music production.
- The chart indicates a noticeable decline in musical diversity starting around 1968, persisting through the end of the 20th century.
- A brief period of recovery in the early 2000s is evident, indicating a renewed interest in experimenting with diverse musical styles.
- A remarkable and sustained increase in musical diversity is observable from around 2004 to 2011. This period could be associated with the rapid growth of the internet, streaming services, and social media, enabling artists from various backgrounds to gain visibility and reach a global audience.
- The last phase is from 2014 to 2020. The trend highlights a somewhat plateaued diversity after the substantial increase observed in the previous decade.

In summary, the trend of "Musical Diversity" over time reflects the dynamic interplay between technological advancements, industry shifts, and cultural influences.


__Part C__: 

The bar plot illustrates the achievements of 19 prominent artists in U.S. musical history since 1958, showcasing the number of their "ten-week hits." Each bar represents an individual artist, and its height quantifies the count of songs that remained on the charts for an impressive ten weeks or more. The data is thoughtfully sorted from the highest to the lowest count of ten-week hits, offering a clear perspective on the most prolific artists in terms of extended chart presence.

![Ten_Week_Hits_Artists](/wrangling_billboard_top_100/Ten_Week_Hits_Artists.png)

Some insights on the plot:
- The range of artists featured on the plot spans a wide spectrum of musical genres, attesting to the diverse musical talents that have shaped U.S. musical history.
- At the pinnacle of the plot, towering bars represent artists who have achieved extraordinary success in terms of ten-week hit songs. Elton John, for instance, stands out with an impressive count of 52 such hits, signifying his enduring popularity and influence across generations.
- The bar plot encapsulates the legacies of musical legends such as Michael Jackson and The Rolling Stones. Their counts of ten-week hits provide a glimpse into the enduring appeal and lasting impact of their contributions to music.

In summary, the bar plot not only showcases the achievements of artists in terms of ten-week hits but also offers a captivating narrative of the ever-evolving world of U.S. musical history.


## Visual story telling part 1: green buildings
The code provides a visual exploration of the rent distributions for green and non-green buildings and investigates whether the building class (Class A) could be a confounding variable in the relationship between green certification and rent.
Please find the code here:
<a href="https://github.com/dongdanyu/ml_final_project/blob/main/green_buildings/greenbuildings_updated.ipynb">green buildings</a>


**We can start by validating what the excel guru found in his analysis** 

![Green_Median_Rent](/green_buildings/Green_Median_Rent.png)

The median rent for green buildings is indeed $2.6 higher than the non-green ones

**Let's look at the variation of rent by each of the variables.** 

Starting with the numerical variables first:

![Size](/green_buildings/Size.png)

![Empl_gr](/green_buildings/Empl_gr.png)

![Leasing_Rate](/green_buildings/Leasing_Rate.png)

![Stories](/green_buildings/Stories.png)

![Age](/green_buildings/Age.png)

![Cluster](/green_buildings/Cluster.png)

![Cd_total_07](/green_buildings/Cd_total_07.png)

![Hd_total07](/green_buildings/Hd_total07.png)

![Total_dd_07](/green_buildings/Total_dd_07.png)

![Precipitation](/green_buildings/Precipitation.png)

![Gas_Cost](/green_buildings/Gas_Cost.png)

![Electricity](/green_buildings/Electricity.png)

![Cluster_rent](/green_buildings/Cluster_rent.png)

Overall, we can say that the rent has a positive relationship with leasing rate and cluster rent.

**Now, let's look at the categorical variables:**

![Renovated](/green_buildings/Renovated.png)

![Class_a](/green_buildings/Class_a.png)

![Leed](/green_buildings/Leed.png)

![Energystar](/green_buildings/Energystar.png)

![Net](/green_buildings/Net.png)

![Amenities](/green_buildings/Amenities.png)

**From the above graphs we can draw the following conclusions:**

Renovated buildings draw lower rent

Class a buildings draw higher rent

Buildings with net contract draw lower rent

**Now, we can check the following hypothesis to see if something else is causing the higher median rent in case of green buildings:**

Are non-renovated building over-represented among Green buildings?

Are Class a buildings over-represented among green buildings?

Are buildings with net contract under-represented among green buildings?

**Let's start with renovated vs non-renovated**

![renovated_2](/green_buildings/renovated_2.png)

So, non-green buildings have much higher proportion of renovated buildings which draw lower rent

**Let's look at Class_a**

![Class_A_2](/green_buildings/Class_A_2.png)

Disproportionate majority of Green buildings are Class A

**Net Contract**

![Net_2](/green_buildings/Net_2.png)

No major difference in net contract buildings between green and non-green buildings

**So, we can safely conclude that the overrepresentation of Class A buildings among the Green buildings are probably causing the median rent of the latter to inflate.**

**In order to adjust for such a confounder we can look specifically at the median rent among non-class a buildings within Green and non-Green buildings**

![Class_A_3](/green_buildings/Class_A_3.png)

When we look at non-Class A buildings, the Green buildings are only $0.25/sq ft/year higher than the non-Green buildings. If we multiply that by 250,000 sq.ft. we get: $62500/year

If we now divide the premium of $5 million by $62,500, we get: 80 years

**Conclusion:** 

It would take 80 years to recuperate the costs incurred to get Green certification which does not seem to be a viable deal. Thus, the project is not worth from an economic perspective.



## Visual story telling part 2: Capital Metro data

The jupyter notebook with the code for this problem can be found here - <a href="https://github.com/dongdanyu/ml_final_project/blob/main/capmetro_UT/capmetro_UT_updated.ipynb">Capital UT</a>

**We can first look at average boardings and alightings of each of the days by hour**

![Boardings_day_hour](/capmetro_UT/Boardings_day_hour.png)

The boarding pattern makes sense as the frequency is the highest between 12 noon to 7 PM which is when students are most likely to travel to their schools and back home

![Alightings_day_hour](/capmetro_UT/Alightings_day_hour.png)

There seems to be something off with the alighting data as it is completely contradictory to the boarding pattern. Volume of alighting peaks around 8 AM in the mornin when majority of the people have not even boarded the bus.

**Therefore, for the purpose of our analysis, we will ignore alighting data.**

**Let us now look at the impact of temerature on boardings**

![Boardings_Temp](/capmetro_UT/Boardings_Temp.png)

As we can see, boardings are much lower during low temperatures and become more frequent during higher temperatures.

**Let's now look at variation of boardings by months**

![Boardings_Month](/capmetro_UT/Boardings_Month.png)

Avg Boardings in October is slightly higher than the other two months

![Boardings_Month_Hour](/capmetro_UT/Boardings_Month_Hour.png)

Hourly pattern of boardings in each of the months is almost the same

**Overall, we can conclude that boardings are likely to be higher during the month of October on weekdays between 12 noon to 7 PM especially when the temperature is higher.**


## Clustering and dimensionality reduction  

I have conducted a thorough analysis of the vinho verde wine dataset using dimensionality reduction techniques (PCA and t-SNE) as well as K-Means clustering. The code and visualizations can be found in
<a href="https://github.com/dongdanyu/ml_final_project/blob/main/clustering_dimensionality_reduction/clustering.ipynb">Clustering and dimensionality reduction</a>

**Principal Component Analysis (PCA):**

Upon applying PCA to the standardized chemical properties, I visualized the results in the PCA plot does indeed show clusters forming based on the wine type (red and white). However, there is an observation to be made regarding the structure of the clusters. The red clusters and the blue cluster borders appear to be attached together, with limited separation. This suggests that while PCA does exhibit some level of clustering.

![pca](/clustering_dimensionality_reduction/diagram/pca.png)


**t-Distributed Stochastic Neighbor Embedding (t-SNE):**

In contrast, t-SNE revealed remarkable results in the t-SNE plot demonstrates a different outcome. Here, the red clusters and the blue cluster borders are visually separated, with a distinct gap in the middle. This separation is a notable feature of the t-SNE visualization and indicates a clearer distinction between red and white wines based on their chemical properties.


![tsne_type](/clustering_dimensionality_reduction/diagram/tsne_type.png)

While both PCA and t-SNE exhibit clustering tendencies, the unique separation exhibited by t-SNE further solidifies its effectiveness in distinguishing between red and white wines based on the unsupervised information contained in the data's chemical properties.

Furthermore, I employed t-SNE to create a plot that attempts to segregate wines based on quality. However, this particular plot does not exhibit a substantial separation between higher and lower quality wines. So my unsupervised technique cannot capable of distinguishing the higher from the lower quality wines

![tsne_qaulity](/clustering_dimensionality_reduction/diagram/tsne_quality.png)


**K-Means Clustering with t-SNE:**

The K-Means clustering plot shares a resemblance to the t-SNE plot. This similarity strengthens the notion that t-SNE captures the natural groupings effectively, as K-Means aligns with its outcomes.

![kmeans](/clustering_dimensionality_reduction/diagram/kmeans.png)
 
**Conclusion:**

Based on the analysis, it is evident that t-SNE is the most suitable dimensionality reduction technique for this dataset. It effectively separates red and white wines, showcasing its ability to distinguish categories with clear natural separation. However, it seems that the chemical properties alone may not be sufficient to distinctly cluster wines by quality. The K-Means clustering results further support the patterns observed in the t-SNE plot.


## Market segmentation

You can find the complete code and analysis in my GitHub repository: <a href="https://github.com/dongdanyu/ml_final_project/blob/main/market_segmentation/market.ipynb">Market Segmentation</a>

To begin the market segmentation, I conducted a correlation matrix analysis and visualized it as a heatmap. The heatmap revealed strong correlations between certain variables, such as "college_unit" and "online_gaming," as well as "personal_fitness" and "health_nutrition." Additionally, some moderate correlations, like 0.6 between "beauty" and "fashion," were observed.

![heatmap](/market_segmentation/heatmap.png)

Afterwards, I performed data preprocessing by dropping columns that weren't relevant for the segmentation analysis. These columns include 'chatter,' 'spam,' 'adult,' and 'Unnamed: 0.' The 'Unnamed: 0' column, which represents user names, was omitted since it doesn't contribute to the analysis. The other dropped columns contain an "uncategorized" label meant to capture posts that don't fit within the listed interest categories.

Next, I employed the K-Means clustering algorithm to uncover distinct market segments. I began by determining the optimal number of clusters (k) using the elbow method.

![kvalue](/market_segmentation/kvalue.png)

Based on the elbow method plot, I selected k=5 as the optimal number of clusters.

Subsequently, I generated a cluster plot that visually depicts the segments:

![cluster](/market_segmentation/cluster.png)


![clustervalue](/market_segmentation/clustervalue.png)


Upon analyzing the clusters, I derived the following summaries:

Cluster 0: This cluster seems to have a relatively high emphasis on topics related to "photo_sharing," "food," "parenting," and "personal_fitness," with moderate values for other topics. It could represent a cluster of users interested in lifestyle, parenting, and health-related content.

Cluster 1: This cluster has higher values for "politics," "sports_fandom," "automotive," and "dating," indicating potential interest in politics, sports, and dating-related topics.

Cluster 2: This cluster has higher values for "uncategorized," "beauty," "fashion," and "small_business," suggesting a focus on fashion, beauty, and potentially entrepreneurial content.

Cluster 3: This cluster shows significantly higher values for "religion," "parenting," "school," and "personal_fitness," indicating an interest in religious, parenting, educational, and health/fitness content.

Cluster 4: This cluster has relatively lower values across most topics, suggesting a more diverse range of interests without a strong focus on any specific topic.

In summary, the market segmentation analysis has uncovered five distinct clusters, each representing users with varying interests and preferences. These insights can be valuable for targeted marketing strategies and tailored content delivery.


## The Reuters corpus  

The jupyter notebook with the code for this problem can be found here - <a href="https://github.com/dongdanyu/ml_final_project/blob/main/The_Reuters_Corpus/ML Assignemnt - The Reuters Corpus.ipynb">The Reuters Corpus</a>

**What Questions are we trying to answer?**

--> Can the corpus be represented in fewer dimensions?

--> Can we cluster the authors in some distinct groups? How many groups?

--> Can we verify by doing some spot checks if the clustering is justified?

**Approach**

For **dimensionality reduction** we used **PCA** and **t-SNE**. The tfidf_matrix we created has 1000 terms for each author. From 1000 we bring down the number of components to 50. Below is the graph showing that we retain almost all the variance in the original data with just 50 components.

![Cumulative_Variance](/The_Reuters_Corpus/Cumulative_Variance.png)

Thereafter, we run t-SNE on the 50 principal components to generate 2 t-SNE components.

For **Clustering** we used the **K-means clustering** with number of clusters being 11. Below is the graph justifying our choice of K (number of clusters):

![Elbow_Plot](/The_Reuters_Corpus/Elbow_Plot.png)

**Results**

Below is the scatter plot of clusters on 2-dimensional t-SNE feature space:

![Clusters_Plot](/The_Reuters_Corpus/Clusters_Plot.png)

**We did some spot checks on some of the clusters:**

In cluster 3, the 3 authors are - Heather Scoffield, Lydia Zajc & Darren Schutteler. All 3 of them write articles on Canadian markets.
In cluster 5, the 3 authors are - Alan Crosby, John Mastrini and Jan Lopatka. All 3 of them write about Czech Republic.

**We also tried to get the most frequent word in each of the clusters. Below is the list:**

![Cluster_Words](/The_Reuters_Corpus/Cluster_Words.png)

This gives us an idea of what are some of the common terms used by authors in each of the clusters thus indicating how and why they have been clustered. For example - Cluster 7 are most likely to be authors who write on China and adjoining region while Cluster 10 authors most likely write about France.

**Conclustion**

The 50 authors can be divided roughly into 11 clusters. While the commonality among the authors are clear in case of some authors, in case of others it is not so clear.

Cluster 0 - Writes about tech companies or tech in general

Cluster 1 - Writes about telecom sector - British or Japan

Cluster 2 - Writes about Chinese markets

Cluster 3 - Writes about Canadian markets

Cluster 4 - Writes about British markets

Cluster 5 - Writes about Czech Republic

Cluster 6 - This group is a little unclear. Some write about south American markets while others about Russia and some about Cocoa trade at Ivory coast.

Cluster 7 - Writes about China and adjoining region

Cluster 8 - Writes about auto markets

Cluster 9 - Writes about Australian markets

Cluster 10 - Writes about French markets


## Association rule mining

The RMD file with the code for this problem can be found here - <a href="https://github.com/dongdanyu/ml_final_project/blob/main/Association_Rule_Mining/ML Assignemnt - Association Rule Mining.RMD">Association Rule Mining</a>

Since the objective of this exercise is to find some interesting association rules for the groceries baskets, as a basic EDA we tried to see the top 20 items most frequently bought by customers.

![Top_Items](/Association_Rule_Mining/Top_Items.png)

We can see that whole milk, other vegetables , rolls/buns etc. are the most frequent purchases. These items are likely to show up with high betweenness.

There are total 1582 association rules when we limit the # of items in the basket to 4.

![All_Rules](/Association_Rule_Mining/All_Rules.png)

We can also look at the plots for these rules

![All_Rules_Plot](/Association_Rule_Mining/All_Rules_Plot.png)

We notice that high lift rules tend to have low support

We can also plot lift vs support with color scale denoting confidence

![All_Rules_Plot_2](/Association_Rule_Mining/All_Rules_Plot_2.png)

Let's now look at the two-key plot of confidence vs support with legends denoting size of the basket

![Two_Key_Plot](/Association_Rule_Mining/Two_Key_Plot.png)

Based on the above plots we decided to zero down on association rules where lift>2 and confidence>0.5 using Gephi.

![Groceries](/Association_Rule_Mining/Groceries.png)

As expected whole milk and other vegetables show up as having highest betweenness. Additionally, we can see some interesting associations like:

--> People are likely to buy ham when they buy white bread

--> People are likely to buy a salty snack when they buy fruit/vegetable juice

--> Bottled beer is usually bought with soda or bottled water 

--> Waffles are usually bought with chocolates

## Image classification with neural networks

The jupyter notebook with the code for this problem can be found here - <a href="https://github.com/dongdanyu/ml_final_project/blob/main/Image_Classification_With_Neural_Networks/ML Assignment - Image classification with neural networks.ipynb">Image Classification With Neural Networks</a>

Below is a brief summary of the neural network model that I used:

**Model Structure** - The input x goes through the first convolutional layer, followed by a ReLU activation function. Max pooling is applied using a 2x2 window after the first convolution. The result is passed through the second convolutional layer, followed by another ReLU activation and max pooling. The tensor is then flattened using view() to match the shape expected by the fully connected layers. The tensor passes through the first fully connected layer with a ReLU activation. Finally, the tensor passes through the second fully connected layer to produce the final output.

**Overall Test accuracy** - We got a test accuracy of 82.26%. Below is a confusion matrix of true class vs predicted class and corresponding proportions. We are showing proportions as the number of images are not equal in each class.

![Confusion_Matrix](/Image_Classification_With_Neural_Networks/Confusion_Matrix.png)

Overall, the model does a decent job except in some cases like some of the highways and some herbaceous vegetation getting misclassified as permanenet crop and vice-versa and some of the rivers getting mis-classified as highways.

Below are a few example images and their corresponding true and predicted class

![Examples](/Image_Classification_With_Neural_Networks/Examples.png)

In the given 5 examples, we can see that the prediction is correct in all but the last case where a highway gets mis-classified as herbaceous vegetation.

