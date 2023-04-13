# TGT-hack
## ⌛ Task
Most of the hydrocarbons we extract from the ground. In the production of hydrocarbons, the appearance of sand is very dangerous because it can cause expensive repairs. In oreder to save company money and time, we had to classify audio data in oreder to find which recorded falling sand on the pipe. 

💰 The first place prize was 150.000 rubles. Second and third got 100.000 and 50.000 rubles.

## 💾 Data
Audio data were recorded in laboratory and already presented as csv file. Grains of sand had different size, also there was different speed of wind. Some grains were mixed with gases or water. Recording time was different. Values were normalized from -1 to 1 and audio sampling rate was 117.2 kHz.

 ## 🔍 EDA 
💡 First of all, I found that the appearance of sand was mostly at the start of the recording. 
Most of records without sand had uniform amplitude and period. However, records with sand were with high volume at the beginning (fall of sand) and quiet at the other parts.
 
### 🔉 Here are the spectrograms

*(second example is with the fall of sand and first is without)*

![image](https://user-images.githubusercontent.com/72515541/231124122-e89feaea-94a0-4e9f-b8dc-9547de8335f1.png)

### 🍭 New features 
That's why I created some features, which were showing whether there was a difference of amplitudes and whether it was at the beginning. And of course I added important features like mean, median, module sums and others

*Here is their corellation* 

![image](https://user-images.githubusercontent.com/72515541/231127911-b1609e48-1a19-4629-9cff-67e5d8eb6827.png)

***🏆 As I saw later, 8 of 10 most important features for models were created by myself***


### Class distribution
![image](https://user-images.githubusercontent.com/72515541/231126942-64000850-775c-471b-866b-b7671c5ada81.png)

As you can see, the count of target class was 6 times smaller. I solved this problem using library NearMiss which deletes similar samples of majoritarian class. However, some models I trained with of all of the data.

## Models

I used *😼CatBoost, 🦄LightGBM* and *👽XGBoost*

🎯 The best scores **(~0.95 f1)** using cross validation after tuning all of the models with GridSearch were obtained by CatBoost and XGBoost.

However, CatBoost was finding records with sand better than XGBoost (see the consusion matrix). That's why I decided to stack them and Catboost got more weight (0.6).

![image](https://user-images.githubusercontent.com/72515541/231132851-f9285023-a090-4222-af62-767023f89de0.png)
![image](https://user-images.githubusercontent.com/72515541/231132775-6f389bb8-8c88-4368-b6d7-bf4846d5def8.png)



# 📣 Result

Public score was **0.96433**.

This solution is 16 out of more than 100.



