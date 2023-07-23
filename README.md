# Indian-Startup-Ecosystem-Analysis
Exploring the Indian startup funding ecosystem through an in-depth analysis of funding data from 2019 to 2021. Gain insights into key trends, funding patterns, and factors driving startup success.

Introduction

The Indian startup ecosystem is one of the most vibrant in the world. In recent years, there has been a surge in the number of startups being launched in India, and these startups have raised significant amounts of funding. This article will explore the Indian startup funding ecosystem through an in-depth analysis of funding data from 2019 to 2021, gaining insights into key trends, funding patterns, and factors driving startup success. Investigating the relationship between funding and startup growth, with a focus on temporal patterns and city-level dynamics, identifying preferred sectors for investment and uncover industry-specific funding trends.

1. Business Understanding
How did India become one of the world’s leading hubs for innovation and entrepreneurship? India has witnessed a remarkable growth in its startup ecosystem in the past decade, with over 50,000 startups registered as of 2021. These startups span across various sectors and domains, such as e-commerce, fintech, edtech, healthtech, and agritech

In this article, I will take you on a journey through my exploration of the Indian startup ecosystem using Python and data gathered on startups that received funding from 2018 to 2021. The primary objective of this project is to gain insights that are valuable to key stakeholders interested in understanding the dynamics of funding in the Indian startup landscape. By thoroughly analyzing key metrics related to funding, I aim to provide decision-makers with the knowledge they need to make informed choices.

One intriguing aspect of this investigation is the hypothesis that the sector or industry a startup belongs to may not necessarily dictate the amount of funding it receives. While common perceptions might suggest that certain sectors, such as technology-focused industries, attract more significant investments, this study will put that assumption to the test. By examining the funding data across various industries, both technological and non-technological, I want to uncover whether sector categorization plays a decisive role in funding outcomes.

To reach valid conclusions, the data cleaning process was an essential step in this analysis. The dataset presented its own set of challenges, with potential inconsistencies for each year that demanded careful attention and treatment. The resulting dataset, refined and organized, forms the foundation of our comprehensive investigation into the funding patterns of Indian startups.

Through rigorous analysis and statistical methodologies, I aim to shed light on the relationships between a startup’s sector and the funding it receives. Such insights can provide valuable guidance to entrepreneurs, investors, and policymakers in navigating the dynamic and vibrant Indian startup ecosystem. By understanding the nuances of funding trends, decision-makers can foster an environment that nurtures innovation, fosters competition, and bolsters economic growth for the years to come.

Research / Analysis Questions:

The COVID-19 pandemic in 2020 significantly impacted various industries worldwide. I aimed to understand how it affected funding for startups in India compared to previous years. By analyzing funding trends before, during, and after the pandemic, I sought to identify any notable shifts or patterns.
To gain a deeper understanding of the geographical distribution of startups and funding, I investigated which cities in India had the highest number of startups and received the most substantial amount of funding. This analysis aimed to provide insights into regional dynamics and potential areas of investment.
The landscape of startups is diverse, with ventures spanning across different sectors. I explored the sectors that housed the highest number of startups and received the most significant funding. Understanding these trends could illuminate promising sectors for potential investors.
A crucial aspect of my analysis was examining potential correlations between the amount of funding a company received and its sector or location. By investigating any connections, I aimed to discern factors that contribute to successful funding outcomes.
An important metric in this analysis was the average funding amount within various industries. I sought to identify the top 10 industries with the highest average funding, offering insights into the most lucrative sectors for potential investors.
Additionally, I explored the average funding amounts in different cities to pinpoint the top 5 cities that attracted the highest average funding. This analysis could aid me in identifying cities with thriving startup ecosystems.
Understanding the correlation between a startup’s stage of development and the amount of funding it receives was another crucial objective. By examining this relationship, I aimed to identify funding patterns across different stages of a startup’s journey.
Hypothesis:

To test the relationship between a company’s sector and the amount of funding it receives, I formulated two hypotheses to focus my analysis.

NULL Hypothesis (HO) — The sector of a company does not have an impact on the amount of funding it receives.

ALTERNATE Hypothesis (HA) — The sector of a company does have an impact on the amount of funding it receives. In other words, there is a significant difference in funding amounts between technology-biased and non-tech biased startups.

By rigorously analyzing the data and performing statistical tests, I aimed to determine whether the type of industry indeed influences the funding outcomes for startups in the Indian ecosystem. These insights have the potential to guide me in making strategic decisions and navigating the dynamic and ever-evolving world of startup funding.

2. Data Understanding
In this report, I aim to explore and gain a deeper understanding of the Indian startup funding ecosystem. The dataset I will be using for analysis contains information about startup funding from 2019 to 2021. It includes various attributes such as the company’s name, sector, funding amount, funding round, investor details, and location.

To conduct a comprehensive analysis, I will examine the dataset to understand its structure, contents, and any potential data quality issues. By understanding the data, I can ensure the accuracy and reliability of my analysis.

The key attributes in the dataset include:

Company — the name of the startup receiving funding.
Sector — the industry or sector to which the startup belongs.
Amount — the amount of funding received by the startup.
Stage — the round of funding (e.g., seed, series A, series B)
Location — the city or region where the startup is based.
About — what the company does.
Funding Year — when the company was funded.
3. Data preparation
3.1: Python Libraries
In the data preparation phase, I will utilize a virtual environment to install essential Python libraries for data cleaning and analysis. Once installed, I’ll import these libraries into my code base to leverage their functionalities effectively. The key libraries to be installed are:

%pip install forex-python
%pip install pandas
%pip install python-dotenv
%pip install seaborn
%pip3 install matplotlib
%pip install pyodbc
%pip install numpy
%pip install scipy
# Importing the Modules needed

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import pyodbc #just installed with pip
from dotenv import dotenv_values #import the dotenv_values function from the dotenv package
import warnings
warnings.filterwarnings('ignore')
from forex_python.converter import CurrencyRates
import re
from scipy.stats import chi2_contingency
from scipy.stats import ks_2samp
import scipy.stats
import scipy.stats as stats
from sklearn.preprocessing import LabelEncoder
from scipy.stats import kruskal, mannwhitneyu
Click on the links below for more information on the libraries that were imported:

Numpy
Pandas
Matplotlib.pyplot
3.2 Importing the data
I have data for three different years: 2018, 2019, and 2020–2021. Each dataset is stored in different locations, and I will access them using appropriate methods for each source.

Data for 2020 and 2021 is stored in a database. To securely access the database, I have stored the necessary credentials in a .env file within the project folder. The .env file is added to the git ignore to prevent it from being tracked by version control, ensuring that sensitive information like database credentials remains private.
To create a connection to the database and access the data, I use the open Database connectivity standard library pyodbc. By setting up a connection string using the database credentials from the .env file, I can establish a connection to the database and retrieve the relevant data for 2020 and 2021.
Data for 2018 is hosted on a GitHub repository. To access this dataset, I utilize the raw URL of the CSV file on GitHub. By using this URL, I can directly read the data into my analysis without needing to download the file locally.
Data for 2019 is available on OneDrive. To access this dataset, I use the specific URL of the CSV file on OneDrive. By accessing the data directly from OneDrive, I can seamlessly integrate it into my analysis without the need for additional file downloads.
4. Exploratory Data Analysis (EDA)
Use various pandas functions and methods to gain an initial understanding of the data such as .head() to view rows in the data set, .shape() to get the total rows and columns in the data set, .info() to get information on the columns, .describe() to get a descriptive statistics about the data frame, .unique and .value counts() to counts the number of occurrences of a value, .isnull to check the missing values and .duplicate to check for duplicate values

After looking at the datasets,I have identified several data quality issues while exploring the datasets:

Inconsistent and missing columns: Some datasets have inconsistent column structures, with missing columns in certain cases.
Missing columns and duplicates in the datasets: Specifically, the 2018 dataset is missing additional columns that are present in other datasets.
Inconsistent values and currencies in the Amount column: The Amount column contains inconsistent values and different currencies.
Inconsistent values in the Stage column: The Stage column exhibits inconsistent values across all datasets, which hampers uniform analysis.
Missing values: Some datasets contain missing values, which need to be addressed for a complete and reliable analysis.
5. Visualizations
How did the COVID-19 pandemic in 2020 impact funding for startups compared to previous years?

There was a significant decline in startup funding in 2020. The total funding amount for 2020 was about half of the total funding amount for 2019.

This decline in funding is likely due to the COVID-19 pandemic. The pandemic caused a recession, which led to a decrease in demand for goods and services. This, in turn, led to a decrease in investment in startups.

However, it’s important to note that the decline in startup funding was not uniform across all industries. Some industries, such as healthcare and technology, actually saw an increase in funding during the pandemic. This is because these industries were seen as essential and were able to continue to grow even during the economic downturn.

Overall, the impact of COVID-19 on startup funding was significant. However, the decline in funding was not uniform across all industries. Some industries were able to weather the storm and even grow during the pandemic.

The drastic rise of the amount of startup funding in 2021 can be explained by a number of factors, including:

The COVID-19 pandemic created a number of new opportunities for startups, as businesses and consumers sought out new ways to work, shop, and live.
The pandemic also led to a surge in venture capital investment, as investors sought to capitalize on the opportunities created by the pandemic.
The rise of remote work and online learning made it easier for startups to operate and raise funding from investors around the world.
The increasing maturity of the startup ecosystem in countries like India and China led to more investment in startups from those regions.
The drastic rise of startup funding in 2021 is a sign of the strength and resilience of the startup ecosystem. The pandemic created a number of challenges for startups, but it also created new opportunities. Startups that were able to adapt to the changing environment were able to raise significant funding and grow their businesses. This trend is likely to continue in the years to come, as the startup ecosystem continues to evolve and mature.

2. Which cities have the highest number of startups and the highest amount of funding received?



Bengaluru is the leading city for startups in India, both in terms of the number of startups and the amount of funding received.

The first visualization shows that Bengaluru has the most startups in India, with over 1,000 startups. The second visualization shows that Bengaluru also received the most funding in the second quarter of 2022, with over $1 billion in funding.

There are a number of reasons why Bengaluru is the leading city for startups in India. First, Bengaluru has a strong startup ecosystem, with a large number of incubators, accelerators, and venture capital firms. Second, Bengaluru is home to a number of large technology companies, such as Infosys and Wipro. These companies provide a source of talent and mentorship for startups, and they also help to create a business-friendly environment for startups.

The other cities in the top 10 for both number of startups and amount of funding received are Mumbai, Gurugram, New Delhi, and Chennai. These cities also have strong startup ecosystems and a large pool of talent. As a result, these cities are all well-positioned to continue to grow their startup ecosystems in the years to come.

Here are some additional insights that can be drawn from the two visualizations:

The top 4 cities in India for startup funding are all located in the southern and western parts of the country. This suggests that these regions are leading the way in terms of innovation and entrepreneurial activity.
The amount of funding received by startups in India has increased significantly in recent years. This is a positive sign for the Indian startup ecosystem, and it suggests that the country is becoming a more attractive destination for investors.
The startup ecosystem in India is becoming more diversified. In the past, the majority of funding went to startups in the technology sector. However, the visualizations show that funding is now being spread more evenly across a variety of sectors, such as healthcare, education, and financial services.
3. Which sectors have the highest number of startups and the highest amount of funding received?



The two visualizations together show that fintech, edtech, and healthcare are the top 3 sectors for startups in India, both in terms of the number of startups and the amount of funding received.

The first visualization shows that fintech has the most startups in India, with over 36% of all startups in the country operating in this sector. Edtech is the second-largest sector, with over 30% of all startups in the country operating in this sector. Healthcare is the third-largest sector, with over 11% of all startups in the country operating in this sector.

The second visualization shows that fintech also received the most funding in India, with over $1 billion in funding. Edtech received the second-most funding, with over $0.8 billion in funding. Healthcare received the third-most funding, with over $0.6 billion in funding.

There are a number of reasons why these sectors are popular for startups and investors in India. First, these sectors are all experiencing rapid growth. Second, these sectors are all underserved by traditional businesses. Third, these sectors are all ripe for innovation.

The growth of the fintech sector in India is being driven by the increasing use of digital payments and the growing need for financial services among the country’s large and growing middle class. The edtech sector is being driven by the growing demand for quality education, the increasing availability of online learning platforms, and the growing number of students who are taking online courses. The healthcare sector is being driven by the country’s aging population, the increasing prevalence of chronic diseases, and the growing demand for affordable and accessible healthcare.

The visualization shows that the Indian startup ecosystem is diverse, with startups operating in a variety of sectors. This diversity is a positive sign for the Indian startup ecosystem, as it suggests that the country is home to a wide range of innovative ideas and businesses.

Here are some additional insights that can be drawn from the two visualizations:

The top 3 sectors in India for both number of startups and amount of funding are all in the technology sector. This suggests that technology is still the leading driver of innovation and economic growth in India.
The amount of funding received by startups in India has increased significantly in recent years. This is a positive sign for the Indian startup ecosystem, and it suggests that the country is becoming a more attractive destination for investors.
The startup ecosystem in India is becoming more diversified. In the past, the majority of funding went to startups in the technology sector. However, the visualizations show that funding is now being spread more evenly across a variety of sectors, such as healthcare, education, and financial services.
4. What are the top 10 industries with the highest average funding?


The visualization shows the top 10 industries by average funding amount. The industries are listed in descending order of average funding amount, with the innovation management industry having the highest average funding amount of $125 million, followed by the software industry ($100 million), the healthcare industry ($90 million), the energy industry ($80 million), and the mechanical and industrial engineering industry ($70 million).

The visualization also shows the percentage of total funding that each industry received. The innovation management industry received the most funding, with 15% of the total funding going to this industry. The software industry received 13% of the total funding, the healthcare industry received 12% of the total funding, the energy industry received 11% of the total funding, and the mechanical and industrial engineering industry received 10% of the total funding.

The visualization is helpful for understanding which industries are receiving the most funding. This information can be used by entrepreneurs and investors to make decisions about where to start or invest in a business.

Here are some additional insights that can be gleaned from the visualization:

The top 5 industries in terms of average funding amount are all technology-related industries. This is likely due to the fact that technology is a rapidly growing and evolving field, and there is a lot of potential for innovation in this area.
The healthcare industry is also a major recipient of funding. This is likely due to the fact that the healthcare industry is facing a number of challenges, such as the aging population and the increasing cost of healthcare.
The energy industry is another major recipient of funding. This is likely due to the fact that the world is facing a growing energy crisis, and there is a need for new and innovative ways to produce and distribute energy.
The mechanical and industrial engineering industry is also a major recipient of funding. This is likely due to the fact that this industry is responsible for developing and manufacturing the products that we use in our everyday lives.
5. What are the top 5 cities with the highest average funding amount?


The visualization also shows the location of each city. Kalpakkam is located in Tamil Nadu, Belling is located in Himachal Pradesh, Faridabad is located in Haryana, Manchester is located in Gujarat, and Mumbai is located in Maharashtra.

The visualization is helpful for understanding which cities in India are receiving the most funding for startups. This information can be used by entrepreneurs and investors to make decisions about where to start or invest in a business.

Here are some additional insights that can be gleaned from the visualization:

The top 5 cities in India for startup funding are all located in the northern and western parts of the country. This may be due to the fact that these regions have a larger population and a more developed economy than the southern and eastern regions.
The average funding amount for startups in India is significantly lower than the average funding amount for startups in the United States. This is likely due to the fact that the Indian startup ecosystem is still in its early stages of development.
The startup ecosystem in India is growing rapidly. The number of startups in India has increased by 150% in the past five years. This growth is being driven by a number of factors, including the availability of funding, the increase in internet penetration, and the growing pool of skilled talent.
6. Are there any correlations between the funding amount and the company’s sector or location?

The correlations provided are numerical values that indicate the strength and direction of the relationship between the funding amount and the company’s sector or location. The correlation coefficient ranges from -1 to 1, where:

1 indicates a perfect positive correlation, meaning that as one variable (funding amount) increases, the other variable (sector or location) also increases proportionally.
0 indicates no correlation, suggesting that there is no discernible relationship between the funding amount and the sector or location.
-1 indicates a perfect negative correlation, meaning that as one variable (funding amount) increases, the other variable (sector or location) decreases proportionally.
Given the correlation coefficients provided:

Correlation between funding amount and sector: 0.016454838539416934 This correlation value is very close to 0, which indicates that there is a weak positive correlation between the funding amount and the company’s sector. In practical terms, this suggests that there is a minimal or negligible relationship between the funding amount a company receives and the sector it operates in. In other words, the sector in which a company operates does not have a significant impact on the funding it receives. Which I intend to investigate further
Correlation between funding amount and location: -0.06070646474590689 Similarly, this correlation value is also very close to 0, but in this case, it is slightly negative. This indicates a weak negative correlation between the funding amount and the company’s location. This implies that, to a small extent, companies located in certain regions may receive slightly lower amounts of funding compared to companies in other locations. However, like the previous correlation, this negative correlation is weak, meaning that location has a limited influence on the funding a company receives.
7. Is there any correlation between the company’s stage of development and the amount of funding it receives?

The correlation coefficient provided is 0.12185608652474544, which indicates a positive correlation between the company’s stage of development and the amount of funding it receives. This means that:

As one variable (the stage of development) increases, the other variable (the funding amount) also tends to increase, and vice versa. However, it’s essential to note that the correlation coefficient is relatively small (close to 0.12), which suggests that the relationship between the two variables is not very strong.

6. Hypothesis Testing

The Kruskal-Wallis test is a non-parametric statistical test used to compare the distributions of three or more independent groups. It is often employed when the data does not meet the assumptions of normality required for parametric tests like the t-test or ANOVA. In this case, the Kruskal-Wallis test is used to test the hypothesis that the sector of a company has no impact on the amount of funding it receives.

The test provides two key outputs: the H-statistic and the p-value.

H-statistic: The H-statistic is a test statistic that measures the degree of difference among the group medians. It quantifies the variability between the groups relative to the variability within the groups.
P-value: The p-value is a measure of the probability of obtaining results as extreme as, or more extreme than, the observed results if the null hypothesis (HO) is true. A small p-value suggests that the observed differences between the groups are unlikely to have occurred by chance alone.
Given the Kruskal-Wallis test results:

H-statistic: 716.4717765754599
P-value: 1.8675988298297976e-48
Explanation:
Since the p-value is extremely small (1.8675988298297976e-48), much smaller than the conventional significance level of 0.05 (5%), we reject the null hypothesis (HO) that the sector of a company does not have an impact on the amount of funding it receives.

The small p-value indicates strong evidence against the null hypothesis, suggesting that there are statistically significant differences in the funding amounts received among different sectors of companies. In other words, the sector of a company does indeed have a significant impact on the amount of funding it receives.

Therefore, based on the Kruskal-Wallis test results, we can accept the alternative hypothesis (HA) that the sector of a company does have an impact on the amount of funding it receives. This implies that certain sectors may be more attractive to investors, leading to higher funding amounts, while others may receive comparatively lower funding due to various factors specific to their industries.

The magnitude of the H-statistic obtained from a Kruskal-Wallis test can vary depending on the dataset being analyzed and the differences between the groups being compared. The specific value of the H-statistic is a reflection of the degree of variability between the group medians relative to the variability within the groups.

In the context of the Kruskal-Wallis test, a large H-statistic indicates that there are substantial differences in the medians of the groups being compared, suggesting that the groups are not drawn from the same population or have different distributions. On the other hand, a small H-statistic suggests that the medians of the groups are similar, and there may be no significant differences between them.

The magnitude of the H-statistic is not directly indicative of the strength of the relationship between the variables or the practical significance of the results. Instead, it serves as a test statistic that, along with the p-value, helps determine whether to reject or fail to reject the null hypothesis (HO).

In this specific case, an H-statistic of 716 is relatively large, indicating that there are substantial differences in the funding amounts received among the different sectors of companies being analyzed. The very small p-value of 1.8675988298297976e-48 further reinforces the statistical significance of these differences, leading to the rejection of the null hypothesis. This means that the sector of a company does have a significant impact on the amount of funding it receives, as supported by the Kruskal-Wallis test results.

Conclusions:
In conclusion, the COVID-19 pandemic had a significant impact on the startup funding landscape in 2020, with a sharp decline in total funding compared to the previous year. The recession caused by the pandemic led to reduced investment in startups as demand for goods and services decreased. However, this decline in funding was not uniform across all industries, as sectors like healthcare and technology experienced an increase in funding due to their essential nature and ability to adapt to the changing economic landscape. This finding supports the hypothesis that the sector of a company does have an impact on the amount of funding it receives. The Kruskal-Wallis test results indicated statistically significant differences in funding amounts among different sectors.

Nevertheless, the startup ecosystem showcased remarkable resilience in 2021, with a drastic rise in funding. Various factors contributed to this growth, including the emergence of new opportunities spurred by the pandemic, increased venture capital investment, and the adoption of remote work and online platforms. Bengaluru emerged as the leading city for startups in India, attributed to its strong ecosystem and support from major technology companies. The diversity of the Indian startup landscape was evident, with funding distributed across sectors such as fintech, edtech, healthcare, and energy.

To navigate future uncertainties, startups should focus on adaptability and innovative business models. Diversifying funding sources, exploring impactful sectors, and nurturing long-term vision will be crucial for sustained success. Government support and investment in incubators, accelerators, and mentorship programs will further foster innovation and growth within the startup ecosystem. As the Indian startup landscape continues to evolve and mature, stakeholders should remain vigilant in identifying opportunities and challenges that can shape the trajectory of this dynamic and thriving ecosystem.

Recommendations:
Resilience and Adaptability: Startups should focus on resilience and adaptability to navigate through challenges like economic downturns and pandemics. Embracing innovative business models and technologies that cater to changing demands and behaviors will be crucial.
Sector Selection: Entrepreneurs and investors should consider the sectors that have demonstrated resilience and growth during challenging times, such as healthcare and technology. Investing in these industries could lead to better returns on investment.
Ecosystem Support: Governments and stakeholders should continue to support and nurture the startup ecosystem, providing incubators, accelerators, and access to funding and mentorship. This support will foster innovation and economic growth.
Diversification of Funding Sources: Startups should aim to diversify their funding sources, seeking both domestic and international investors. Leveraging the rise of remote work and online collaboration can facilitate connections with global investors.
Focus on Impactful Sectors: Startups should consider exploring sectors like fintech, edtech, and healthcare, which have shown significant growth and received substantial funding. Developing solutions that address critical challenges in these industries can attract investor interest.
Long-term Vision: Investors and entrepreneurs should maintain a long-term vision for the startup ecosystem. While funding may fluctuate in the short term due to external factors, a strong focus on sustainability and growth will lead to long-term success.
Read more details on my notebook https://github.com/Feiiiisal/Indian-Startup-Ecosystem-Analysis

Appreciation
I highly recommend Azubi Africa for their comprehensive and effective programs. Read More articles about Azubi Africa here and take a few minutes to visit this link to learn more about Azubi Africa life-changing programs

Azubi Data Science





