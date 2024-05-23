# README 
## Approaches to find the data set:
### 1
The 700 sized dataset : It seems the weight column has become corrupted. For some data points the eight and height have simply been set to be equal and for other the weight is much too low. An 11 year old will not weigh 5.05 kg for instance. If you plot height vs weight you'll see immediately that apart form the line of data-points where height and weight coincides there seems to be no correlation which is highly suspect. link : https://www.kaggle.com/datasets/sulaimanahmed/lung-capacity-data/data <br/>
### 2
Used kaggle to find other dataset, could not find any with name "tidal volume" so I switched to find one with Total Lung Capacity as they both are generally in some fixed proportion so the study on total lung capacity should give same prediction as with Tidal Volume. link: https://www.kaggle.com/datasets/klu2000030172/lung-disease-dataset
### 3
Finally I found a trustable dataset. But accessing the lung volume from the text file was quiet tiresom. link: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9168312/. The text file had rate to air flow $(L/s)$ in regular interval of $10ms$.<u>  After quiet tidal breathing on the spirometer, participants were coached to perform a maximal inhalation followed by a maximal exhalation to residual volume (i.e., plateau), followed by a second maximal inhalation </u>. We would have to figure out which phase is of maximum exhalation noticing the rate of flow going positive and negative and amount of air flown during that time period. 
