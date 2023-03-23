
# JPMorgan Private Banking Challenge

### Problem Statement 
Part I

The COVID-19 pandemic precipitated an abrupt end to many of the catalysts of global growth over the past decade, and underpins a paradigm shift in portfolio asset allocation. Positive equity-bond correlation and a simultaneous drawdown in both asset classes in 2022 have encouraged investors to seek additional sources 
of yield, capital appreciation, and diversification. 

Sean understands the need for diversification but is struggling to determine his portfolio allocation, and would like to seek your team’s advice on a strategic asset allocation that will enable him to achieve his goals. 

Part II

In 2022, the global rate-hiking cycle became increasingly synchronized as central banks became progressively cognizant of inflation. Even as supply chain tightness has eased, markets are still mixed on how sticky inflation may be. Other macro risks such as growth slowdowns in developed markets, global supply-chain decoupling and trade regionalization, and geopolitical tensions will need to be kept in mind. As Sean is focused on his work and does not follow the markets closely, briefly recap what happened in 2022, provide an outlook of 2023, and recommend a tactical asset allocation (1-year horizon) for Sean.

### Data-Driven Approach

Data is key when analysing and understanding financial trends especially in today's volatile and multifaceted market. There is greater emphasis placed on data-driven models especially when forecasting stock/asset-class price movements. 

For example, if one were to predict 10 years worth of price movement (%), one would need to obtain at least 10 years worth of past historical data to train a Machine Learning Model well enough to predict the values well enough. By well enough it means not going too far off from the the actual values, as compromising on this very fact would cost alot in companies. 

### An Aspiring Data Scientist's Approach 

As a proficient Data Analyst solely based on experience in a generic domain, it was intuitive for me to make use of Python's Data Analytics libraries in a code-driven manner. 

As compared to the other data anaytics projects I've worked on, I decided to broaden my focus - covering a range of data science domains like data preprocessing, data engineering and machine learning model deployment. This allowed me to have a full and deep appreciation of the data science hierarchy, by experiencing both the Machine Learning Engineer and Data Analyst roles for this project. 

![image](https://user-images.githubusercontent.com/77159089/227025036-30b0bc54-d884-4a2d-9ed2-f4beef78a28a.png)


The bulk of my work can be found in the Python Notebooks within the concoction of repository files. I made use of Pandas, Matplotlib and Seaborn as my data visualisation of choice, followed by deploying an ARIMA (Auto Regressive Integrated Moving Average) Model to predict stock price movement 10 years into the future. The nature of model used (which I'm sure there are plenty others) is highly dependent on the dataset utilised during the project, which was a univariate time series dataset. ARIMA came naturally as a tool for price forecasting. 

### IWD Data Viz 
![image](https://github.com/Marcus0104/JPMorgan-Hack-2023/blob/main/original_predicted_viz.png)

### TAN Data Viz 
![image](https://github.com/Marcus0104/JPMorgan-Hack-2023/blob/main/original_predicted_viz_TAN.png)

The ARIMA model can be better trained by using a proper train test split, allowing for better accuracy and prediction. The predicted model could mimic the general trend of price movement, however it was unable to determine the peak rise and fall in price movement. 

### Where do I start? 
For starters with or without financial/investing knowledge, I have divided the proposed portfolio into 3 distinct categories: BlueMarket (Blue Chip/Dividends Market), HighRisk, and ValueStocks. The notebooks can be found under the label [Stock]_PriceXTime.ipynb together with the respective datasets in CSV format. 

Additional documents can be found in the Forecast and Invesco QQQ folders. The Forecast folder simply contains predictions done from the current year 2023 up till 2033. These dates are not explicitly defined as indexes, but the ordering follows a chronological order (top to bottom). The Invesco QQQ folder contains my data analysis and machine learning when I first got my hands dirty on the Invesco QQQ ETF through countless trial and errors and familiarising myself with syntax. 

Justification to our methodology and strategy: https://github.com/Marcus0104/JPMorgan-Hack-2023/blob/main/UNIX_Capital_Exe_Summary.pdf

### Closing Remarks

A disclaimer that most of the work done is a work in progress. Due to the tight time budget for the project, most of the code produced was written with the end goal of predicting multiple outcomes, with less of an emphasis toward documentation and thorough Data Visualisation/Analytics. I believe that my work will be able to value-add to anyone interested in pursuing a similar hackathon/challenge in the future, and that it would speak for itself. 
Do feel free to provide me criticism, feedback or comments! 
### 🔗 Connect: LinkedIn 

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/marcus-ng-0104e/)


### Acknowledgements
Shoutout to my peak perf. team: 
Thank you for sharing this opportunity with me! 
 * https://www.linkedin.com/in/james-xfa/
 * https://www.linkedin.com/in/lucas-yap-81a819163/
 * https://www.linkedin.com/in/hillman-hung-a0b0a8256/


