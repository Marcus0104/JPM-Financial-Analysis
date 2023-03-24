
# JPMorgan Private Banking Challenge 
#### Author: Marcus Ng Junhao  
### UNIX CAPITAL Team
* [Lucas Yap - Portfolio Analyst](https://www.linkedin.com/in/lucas-yap-81a819163/)
* [James Teo - Research Analyst](https://www.linkedin.com/in/james-xfa/)
* [Hillman Hung - Quantitative Analyst](https://www.linkedin.com/in/hillman-hung-a0b0a8256/)
* [Marcus Ng - Data Scientist](https://www.linkedin.com/in/marcus-ng-0104e/)

# Table of contents
1. [Introduction](#introduction)
2. [Data-Driven Approach](#approach)
3. [Aspiring Data Scientist's Approach](#datascience)
4. [Parameter Optimisation and Model Deployment](#machinelearning) 
5. [Where do I start?](#begin) 
6. [Closing Remarks](#end) 

### Introduction <a name="introduction"></a>
Part I

Sean's Background Information and Investment Portfolio was provided to our team as a document. 

The COVID-19 pandemic precipitated an abrupt end to many of the catalysts of global growth over the past decade, and underpins a paradigm shift in portfolio asset allocation. Positive equity-bond correlation and a simultaneous drawdown in both asset classes in 2022 have encouraged investors to seek additional sources 
of yield, capital appreciation, and diversification. 

Sean understands the need for diversification but is struggling to determine his portfolio allocation, and would like to seek your team’s advice on a strategic asset allocation that will enable him to achieve his goals. 

Part II

In 2022, the global rate-hiking cycle became increasingly synchronized as central banks became progressively cognizant of inflation. Even as supply chain tightness has eased, markets are still mixed on how sticky inflation may be. Other macro risks such as growth slowdowns in developed markets, global supply-chain decoupling and trade regionalization, and geopolitical tensions will need to be kept in mind. As Sean is focused on his work and does not follow the markets closely, briefly recap what happened in 2022, provide an outlook of 2023, and recommend a tactical asset allocation (1-year horizon) for Sean.

### Data-Driven Approach <a name="approach"></a>

Data is key when analysing and understanding financial trends especially in today's volatile and multifaceted market. There is greater emphasis placed on data-driven models especially when forecasting stock/asset-class price movements. 

For example, if one were to predict 10 years worth of price movement (%), one would need to obtain at least 10 years worth of past historical data to train a Machine Learning Model well enough to predict the values well enough. By well enough it means not going too far off from the the actual values, as compromising on this very fact would cost alot in companies. We also realise that the dataset 

I have broken down the project for each of these stocks into 3 distinct segments: Data Engineering, Data Analytics and Visualisation, building the ARIMA Machine Learning Model, and finally deploying the model to predict stock price movement for each equity in the next 10 years. 

### An Aspiring Data Scientist's Approach <a name="datascience"></a>

As a proficient Data Analyst solely based on experience in a generic domain, it was intuitive for me to make use of Python's Data Analytics libraries in a code-driven manner. 

As compared to the other data anaytics projects I've worked on, I decided to broaden my focus - covering a range of data science domains like data preprocessing, data engineering and machine learning model deployment. This allowed me to have a full and deep appreciation of the data science hierarchy, by experiencing both the Machine Learning Engineer and Data Analyst roles for this project. 

![image](https://user-images.githubusercontent.com/77159089/227025036-30b0bc54-d884-4a2d-9ed2-f4beef78a28a.png)


The bulk of my work can be found in the Python Notebooks within the concoction of repository files. I made use of Pandas, Matplotlib and Seaborn as my data visualisation of choice, followed by deploying an ARIMA (Auto Regressive Integrated Moving Average) Model to predict stock price movement 10 years into the future. The nature of model used (which I'm sure there are plenty others) is highly dependent on the dataset utilised during the project, which was a univariate time series dataset. ARIMA came naturally as a tool for price forecasting. 

### Approximation of Parameters and Model Deployment <a name="machinelearning"></a>
We use the Akaike information criterion (AIC) is a mathematical method for evaluating how well a model fits the data it was generated from.
```python
from itertools import product
import warnings
warnings.filterwarnings('ignore')

# Initial approximation of parameters
Qs = range(0, 2)
qs = range(0, 3)
Ps = range(0, 3)
ps = range(0, 3)
D=1
d=1
parameters = product(ps, qs, Ps, Qs)
parameters_list = list(parameters)
len(parameters_list)

# Model Selection
results = []
best_aic = float("inf")
warnings.filterwarnings('ignore')
for param in parameters_list:
    try:
        model=sm.tsa.statespace.SARIMAX(target['Price Movement(%)'], order=(param[0], d, param[1]), 
                                        seasonal_order=(param[2], D, param[3], 12)).fit(disp=-1)
    except ValueError:
        print('wrong parameters:', param)
        continue
    aic = model.aic
    if aic < best_aic:
        best_model = model
        best_aic = aic
        best_param = param
    results.append([param, model.aic])
```
![image](https://github.com/Marcus0104/JPMorgan-Hack-2023/blob/main/Best%20Model%20Approximation.png)

### TAN Price Test Prediction & Analysis
```python
test = target.loc['1/1/2015':'1/1/2023']
test['forecast'] = best_model.predict()
plt.figure(figsize=(15,7))
test['Price Movement(%)'].plot()
test['forecast'].plot(color='r', ls='--', label='Predicted Price Movement')
plt.legend()
plt.title('Price Movement, By Months')
plt.ylabel('Price Movement(%)')
plt.show()
```
![image](https://github.com/Marcus0104/JPMorgan-Hack-2023/blob/main/original_predicted_viz_TAN.png)

### A Step into the Future
```python
# format: 1/3/2023 DAY/MONTH/YEAR to be converted into a datetime object 
startdate = dt.date(int(2023), int(3), int(1))

date_list = [] # concatenate at the bottom of the dataset 
while startdate < dt.date(int(2033), int(3), int(1)):
    startdate += timedelta(days=31)
    formatted_date = startdate.strftime("%d-%m-%Y")
    date_list.append(formatted_date) 
print(date_list)
future = len(date_list) 
export = best_model.forecast(steps=future)
export.to_csv(r'TAN_PriceXTime.csv', index=True, header=True)
```

Ontop of the parameter optimisation, the ARIMA model can be better trained by using a proper train test split. <br> 
With time, the model accuracy can definitely be improved, allowing for better model accuracy.

### Where do I start? <a name="begin"></a>
For starters with or without financial/investing knowledge, I suggest reading up on basic investing to gain prior domain knowledge. I have segmented our proposed portfolio into 3 distinct categories: BlueMarket (Blue Chip/Dividends Market), HighRisk, and ValueStocks. The notebooks can be found under the label [Stock]_PriceXTime.ipynb together with the respective datasets in CSV format. 

Additional documents can be found in the Forecast and Invesco QQQ folders. The Forecast folder simply contains predictions done from the current year 2023 up till 2033. These dates are not explicitly defined as indexes, but the ordering follows a chronological order (top to bottom). The Invesco QQQ folder contains my data analysis and machine learning when I first got my hands dirty on the Invesco QQQ ETF through countless trial and errors and familiarising myself with syntax. 

Justification to our methodology and strategy: <br>
https://github.com/Marcus0104/JPMorgan-Hack-2023/blob/main/UNIX_Capital_Exe_Summary.pdf

### Closing Remarks <a name="end"></a>

A disclaimer that most of the work done is a work in progress. Due to the tight time budget for the project, most of the code produced was written with the end goal of predicting multiple outcomes, with less of an emphasis toward documentation and thorough Data Visualisation/Analytics. I believe that my work will be able to value-add to anyone interested in pursuing a similar hackathon/challenge in the future, and that it would speak for itself. 
Do feel free to provide me criticism, feedback or comments! 
### 🔗 Connect: LinkedIn 

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/marcus-ng-0104e/)
