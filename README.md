# README 
## Approaches to find the data set:
### 1
The 700 sized dataset : It seems the weight column has become corrupted. For some data points the eight and height have simply been set to be equal and for other the weight is much too low. An 11 year old will not weigh 5.05 kg for instance. If you plot height vs weight you'll see immediately that apart form the line of data-points where height and weight coincides there seems to be no correlation which is highly suspect. link : https://www.kaggle.com/datasets/sulaimanahmed/lung-capacity-data/data <br/>
### 2
Used kaggle to find other dataset with about 470 data-points, could not find any with name "tidal volume" so I switched to find one with Total Lung Capacity as they both are generally in some fixed proportion so the study on total lung capacity should give same prediction as with Tidal Volume. link: https://www.kaggle.com/datasets/klu2000030172/lung-disease-dataset
### 3
Finally I found a trustable dataset. But accessing the lung volume from the text file was quiet tiresom. link: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9168312/. The text file had rate to air flow $(L/s)$ in regular interval of $10ms$.<u>  After quiet tidal breathing on the spirometer, participants were coached to perform a maximal inhalation followed by a maximal exhalation to residual volume (i.e., plateau), followed by a second maximal inhalation </u>. We would have to figure out which phase is of maximum exhalation noticing the rate of flow going positive and negative and amount of air flown during that time period.
<br> Finally used the second dataset.</br>

## Building Models:
1. Tried Linear Regression: Got very high error, this means that lung capacity is not a linear function of other parameters.
    #### On training sample
    (Yellow points show actual values and blue shows perdicted values)
    [![prev-model-work.png](https://i.postimg.cc/sDVgc9Vk/prev-model-work.png)](https://postimg.cc/5jRJ9zQg)
    #### On testing sample
    (Blue points show actual values and red shows perdicted values)
    [![lin-reg-on-test.png](https://i.postimg.cc/Zq6G22HV/lin-reg-on-test.png)](https://postimg.cc/94Fgqxv7)
2. Tried other ways but those also didn't work well.
3. USED NEURAL NETWORKS FOR REGRESSION<br>
    1. Increasing number of neurons in a dense layer was morw helpful than increasing number of hidden layers.
    2. Tried various combinations and found the best one to be with three dense layers, one input layer and one output layer.
    3. Added some dropout layers to prevent overfitting.
    4. Used StandardScaler to normalize the data which increases model's speed and accuracy.
    5. Used ADAM optimizer.
    6. The model is taking about 20 seconds to train.
    #### Train loss and Test loss with respect to epochs
    [![Train-loss-vs-test-loss.png](https://i.postimg.cc/13Rx2J2Q/Train-loss-vs-test-loss.png)](https://postimg.cc/LnW0ZBmC)  
    #### On training sample
    (Blue points show actual values and red shows perdicted values)
    [![best-model-on-train.png](https://i.postimg.cc/Z5bj4gJw/best-model-on-train.png)](https://postimg.cc/rKH59f04)
    #### On testing sample
    (Blue points show actual values and red shows perdicted values)
    [![best-model-on-test.png](https://i.postimg.cc/02fdWf7D/best-model-on-test.png)](https://postimg.cc/mtPHh7Xg)
## HOW TO RUN THE MODEL
1. Download all the files in the repository.
2. To again train the model, run all the cells.
3. A pre-trained model is already saved, to use this model load the model.
4. Provide the required attributes in the form of csv file that are [FEC1, AGE, SMOKE($1$ for $yes$, $0$ for $no$), O2($0$ or $1$), ABG-P-O2 ($0$ or $1$) , ABG-P-CO2($0$ or $1$), ABG-pH-Level($0$ or $1$), Asthama($1$ for $yes$ $0$ for $no$), Other Diseases($1$ for $yes$ $0$ for $no$), PEFR($0$ or $1$), Risk($0$ or $1$)].
These must be in the specific order give above.
5. You will get the output which is the Lung Tidal Volume in Liters.