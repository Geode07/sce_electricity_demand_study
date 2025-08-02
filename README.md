# Analysis of Changes to Electricity Consumption in the Southern California Edison Service Area

Southern California Edison (SCE) is one of the largest electric utilities in the US, serving most of Southern California. The image below shows the motivation for this project: between 2014 and 2023, the overall amount of electricity consumed by residential SCE customers decreased, despite multiple countervailing factors. Countervailing factors included the global Covid pandemic, a severe drought, and rapid adoption of electric vehicles. 

This project aimed to identify the factors that contributed to this decrease in residential electricity consumption. The attached workbook walks through the EDA, predictive modeling, and interpretation of results.

Initial hypothesis: Weather patterns, population socioeconomic changes, rooftop solar adoption, EV adoption, and hidden investments in energy efficiency caused the downward changes in electricity consumption across the SCE service territory between 2014 and 2023. Specifically, changes in electricity consumption at the residential customer level can be predicted by weather, socioeconomic, rooftop solar adoption, EV adoption, and changes to overall electricity demand in the system over time.

To identify and understand the factors the contributed to this net decrease in residential electricity consumption, I gathered data from a wide range of sources, for tracking electricity consumption, weather conditions, and socioeconomic factors. The data was collected from the following sources: SCE website provides detailed history of electricity consumption by zip code. Open Meteo provides a REST api to download historical weather data. The US census provides detailed socioeconomic data at the zip code level. The Lawrence Berkeley National Laboratory publishes annually a national record of rooftop solar installations by zip code. Lastly, the State of California CPUC also publishes annually a detailed data set of EV registrations by zip code.

The analysis approach was as follows: 
1. Initial phase: perform EDA using covariance matrix, decide which variables to include in initial models, conduct OLS regression to test the hypothesis.
2. Classification modeling phase: develop a logistic regression model, SVM linear model, and SVM nonlinear model. Select the most accurate classification model.

This study applied linear regression, logistic regression, and SVM classification modeling to test the relationship between the change in total kWh and a set of weather and socioeconomic factors. Multicollinearity and overfitting were seen in the linear regression model. Despite these limitations, delta_load_per_account was found to be the most important predictor.

Classification modeling for delta_load_per_account_binary showed that the SVM with the RBF kernel had the highest accuracy and AUC score. Per the logistic regression model, the most important features associated with increasing delta_load_per_account_binary were: TotalkWh, temperature_2m_max, and year. The most important features associated with decreasing delta_load_per_account_binary were: Total accounts, quarter, and cumulative_solar.

Overall, these models are an interesting start to this investigation. In future work, additional data sources will be useful, including more detailed weather data per zipcode and more detailed data about energy efficiency investments. Additionally, removing variables with excessive multicollinearity will be useful.

![SCE Loads](sce-loads.png)
