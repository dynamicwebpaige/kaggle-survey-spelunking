# Machine Learning Cohorts: 
## _A Synthesis_

_“Data Scientist”_, _“Machine Learning Developer”_, _“Deep Learning Engineer”_, _“Data Engineer”_, _“ML Ops Engineer”_, and _“Data Analyst”_ are often overloaded role titles -- and **not necessarily indicative of a user’s day-to-day work, or the tools they are using to accomplish that work**. 

To better understand and characterize these diverse user segments, **we can use tools, libraries, and frameworks referenced in the [Kaggle: State of Machine Learning and Data Science 2020 Survey](https://www.kaggle.com/kaggle-survey-2020) to cluster engineers into cohort groups**. We can also loosely tie these cohorts to their anticipated cloud spend; identify typical tasks each user cohort is responsible for completing; assess compute and storage requirements for each user cohort; and estimate cohort size, based on survey responses. 

## TL;DR 
 
> Survey respondents are overwhelmingly performing **exploratory analysis using small- to medium-sized data sets stored as flat files, on local machines**. Machine learning projects – if ML is being attempted at all – are in **early stages**, using traditional methods that are best-suited for **high-RAM CPU rather than GPU** SKUs (ex: scikit-learn and clustering approaches).  

> Based on responses, **data science teams trend small (0-5 engineers)**, with light rigor on SDLC best practices (ex: version control); and **most data scientists come from non-CS backgrounds**, with minimal programming experience. Preferred tools are overwhelmingly **open-source and non-proprietary**. If Visual Studio Code is being used by survey respondents, it is most often being used for **non-interactive, production machine learning and data science  work**. 

## Data Sources  

The following surveys were included in the analysis: 
 
| Survey | Description | Applicable # (out of total) | Raw Data Available? | Utility |
| ----------- | ----------- | ----------- | ----------- | ----------- | 
| [Kaggle State of Data Science and ML 2020](https://www.kaggle.com/kaggle-survey-2020) | Annual survey of 6-7M registered Kaggle users. Kaggle is the world’s largest online community for machine learning and data science. | 20,036 | Y | ★★★★ |  
| [StackOverflow Developer Survey](https://insights.stackoverflow.com/survey/2020) | Annual survey of StackOverflow users. Not domain-specific; ~8% of respondents indicated doing data-affiliate work (data science, ML, research). | 5,200 | Y | ★ |
| [Python Developers Survey 2020](https://www.jetbrains.com/lp/python-developers-survey-2020/) | Annual survey of Python developers, completed in partnership between the PSF and JetBrains. Not data science and ML-specific, though ~50% of respondents indicate they use Python for EDA. | 15,400 | N | ★★★ |
| [Anaconda Data Science Survey](https://www.anaconda.com/state-of-data-science-2020?utm_medium=press&utm_source=anaconda&utm_campaign=sods-2020&utm_content=report) | Focused survey for data analysts and ML engineers administered by Anaconda. Data not released publicly; but an executive summary is available. | 2,360 | N | ★★★ |
| [SlashData Survey](https://www.slashdata.co/) | Not a domain-specific survey, and not segmented out by tools used. More than half of ML and data science respondents (5K) are hobbyists and students, and just learning how to do ML; not professionals. | 5,009 | N | ★★ |
 
Given the focused nature of the two survey instruments, **the Anaconda survey and the Kaggle surveys were both selected as the most useful for the purpose of this analysis**. The data science and machine learning respondents from the Python Developers Survey (55% of total); the professional data science and machine learning respondents for the SlashData Survey (25% of total); and the data science respondents from the StackOverflow Developer Survey (8% of total) are used as supplemental evidence.  

Though just under a third of total respondents for the Kaggle Survey and the PSF Survey indicated that they were using VS Code, this was found -- through qualitative interviews, as well as from social media scraping and Github issues analysis -- not to be for exploratory data analysis or interactive model building, but rather for **machine learning model deployment**; for **other types of software development or Python library building**; or for **lightweight editing** of Python and markdown files.

![](https://github.com/dynamicwebpaige/kaggle-survey-spelunking/blob/main/Screen%20Shot%202021-06-19%20at%2011.43.18%20AM.png?raw=true)

The data is available to [view via Github's Flat Data](https://flatgithub.com/dynamicwebpaige/kaggle-survey-spelunking?filename=kaggle_survey_2020_responses.csv&sha=25822e0dc1c7e8f354dcc82f59c6247dfc7868df), and to download from the Kaggle website.

## Methods  

The Kaggle survey data was cleaned, and then one-hot encoded for each developer tool based on survey responses. Tools used by less than 10% of respondents were removed from the dataset. We then used UMAP clustering with nearest neighbors of 32 to define clusters of users; six distinct clusters were found and translated into cohorts, with no apparent correlation to self-assigned role title.

![](https://github.com/dynamicwebpaige/kaggle-survey-spelunking/blob/main/clusters.gif?raw=true)

Clusters were validated with the qualitative data in the Anaconda Data Science Survey, as well as with blog and social media posts; StackOverflow issues; and Github issues (for example: ML Ops engineers tend to have backgrounds that fall more commonly on the "software engineering" side of the spectrum).

## Results 

Primary findings from the aggregated survey responses can be found below. The numbers adjacent to each bullet point indicate which survey above (1 through 5) supports each assessment. 
 
## Demographics 

* Many of the survey respondents **do not have a computer science background**, but have been trained in some other domain (physical, natural or biological sciences; statistics; etc.) -- often obtaining a graduate or professional degree. [1,2,3,4] 

* Most survey respondents have been **programming for less than a decade**, and have less than three years of experience with machine learning or software engineering. [1,4] 

* The majority of survey respondents **work in small teams (0-5 engineers)**, or in large communities of practice (20+ engineers). These data scientists are not likely to be using version control systems; but do often **indicate using GitHub as both a place to find code for their experiments, and a way to showcase their work**. [1,4,5] 
 

* Most survey respondents appear to be in their **late 20s or early 30s**, with 60% between 22 and 34. Only 20% are above the age of 40; and there are signs of the numbers skewing even younger, as Generation Z becomes more involved with data science and machine learning work. **Nearly 7% of Kaggle survey data scientists are aged 18-21**, an increase from 5% in 2019. [1,2,4,5] 
 
## Tools

 * **Jupyter products** (JupyterLab and original Jupyter notebooks) **are the overwhelming winner** in terms of IDE use (74.1%), with VS Code, PyCharm, and RStudio neck-in-neck for second place (all around 32%). **It is common for survey respondents to use more than one development environment**. [1,2,3,4,5] 
 
* Survey respondents prefer having a **quick scratchpad that is automatically connected to data sources** and does not require manual authentication. Though free-tier hosted notebooks (ex: Colab, Binder) are used by a subset of respondents, hosting and sharing code externally is not a P0. [1,4] 
 
* Data scientists overwhelmingly use **open-source tools, not proprietary tools**. [1,2,3,4,5] 

## Data 

* Most survey respondents are using **small to medium-sized data sets that can fit in memory**. [1,4] 
 
* These data sets are usually comprised of **local flat files (CSVs, JSON, etc.), or tables exported from relational databases**. Data lakes and non-SQL databases are rarely used, if ever. [1,4] 
 
* Preferred databases are primarily open-source (**PostgreSQL, MySQL, SQLite, etc.**), though a significant number of users are opting for Microsoft SQL Server. [1] 
 
* **Exploratory data analysis is a significant component** of both data science and machine learning work; and is usually done using open-source libraries. _Please note_: EDA is distinct from and a precursor to ETL pipeline-building.[1,4] 
 
* **Little to no** exploratory data analysis is being done using large clusters of machines (Spark, Dask). If these tools are used, it is most commonly by the cohorts that are described in the table below as ML Ops professionals, data engineers, or deep learning engineers. [1,4] 
 

## Algorithms and Methods 
 
* Most survey respondents are doing either **exploratory data analysis, or traditional machine learning with scikit-learn**. These models are most commonly logistic and linear regression; random forests and decision trees; Bayesian methods; and gradient boosted trees. [1,3,4] 
 
* It is common for data scientists to use more than one language – and the usual suspects are **R, Python, and SQL**. [1,2,3,4,5] 
 
* Most survey respondents **are not using automated machine learning (AutoML)** techniques, or experiment management and model orchestration tools (ex: Weights & Biases, MLFlow). [1,4] 
 
## Production and Cloud 
 
* Most survey respondents are **not yet using machine learning in production**, though that number is steadily increasing year over year (28.9% in 2019 compared to 30.8% in 2020). [1,4,5] 
 
* Most survey respondents are **not yet using self-hosted cloud technologies**, though they often leverage third-party hosted notebooks (ex: Colab, Binder). [1] 

Segmenting out Kaggle survey respondents who indicated spending more than $100K (n = 729) on cloud resources, we find that: 

* There are a substantial number of respondents using Power BI and Tableau (22% and 30%, respectively). 
 
* Azure jumps to second place (31%) for survey respondents who indicate that they spend more than $100K on cloud resources. For survey respondents in aggregate, the second most popular cloud is GCP. The most popular cloud for both segments is AWS.
 
* Large-scale cloud customers have even less of a focus on deep learning; if they are using machine learning at all, they are using traditional models. 
 
* Only half of large-scale cloud compute users (49%) are using GPUs - and, even for those users, those GPUs are local. 
 
* Survey respondents who indicated spending $100K or more on cloud resources were more likely to be tenured employees (5+ years of experience). 
 
* The other data points still hold: VS Code is in a distant second place to Jupyter* as an IDE; flat files and relational databases still most common data sources; most teams don’t have machine learning models running in production and are still exploring; etc. 

## Machine Learning User Cohorts

The survey data described above has been used to create a customer cohort table (distilled view below).

_Please note_: this table is not meant to be a comprehensive assessment of each of these cohort groups and the tools they used; just a brief overview. Additional blog posts with a deep dive for each group to follow.

| Cohort | Description | Most Common IDEs |
| ----------- | ----------- | ----------- |
| Beginners (new to programming) | New to programming, data science, and machine learning. Canonical example would be high school and college students. Primary mechanism to learn is video content (Coursera, YouTube, EdX, etc.). | Hosted notebooks (ex: Colab) or Jupyter notebooks |
| Beginners (current software engineers, new to ML) | New to data science and ML, and just beginning to learn. Most commonly come from an app development background. | PyCharm, VS Code, Visual Studio, other software IDE |
| Data Analyst | Use data to help understand business problems or research questions. Minimal (if any) statistics background. | Excel or Google Sheets | 
| Data Scientist – Business, EDA | Use data to help understand business, logistics, or supply chain problems. | Jupyter/JupyterLab, RStudio |
| (Data) Scientist – Academic, EDA | Use data to help understand problems in the physical, biological, social, or natural sciences. | MATLAB, Jupyter/JupyterLab, RStudio |
| Data Scientist – Business, Traditional ML | Just beginning to use machine learning methods to solve business problems, and to complement exploratory data analysis techniques. | Jupyter/JupyterLab, RStudio |
| ML Researcher – Academic, Traditional ML | Just beginning to use machine learning methods to solve research questions, and to complement exploratory data analysis techniques. | Jupyter/JupyterLab, MATLAB, RStudio |
| Deep Learning Researcher (small-scale) | Similar to the traditional machine learning segment; most comfortable with medium-sized data sets and local machines. | Jupyter/JupyterLab, PyCharm |
| ML Framework Builder, or High-Level Deep Learning API Builder | Authors of scikit-learn, Keras, PyTorch Lightning, and other similar tools. | Jupyter/JupyterLab, PyCharm or VS Code |
| Deep Learning Engineer (large-scale) | The NeurIPS, ICML, and ICLR contingent; these are the researchers you would expect to see hired at OpenAI, Google Brain, etc. | Jupyter/JupyterLab, PyCharm or VS Code |
| Deep Learning Framework Builder | Authors of low-level APIs for TensorFlow, JAX, and PyTorch; distributed training frameworks, like Ray; and similar. | PyCharm or VS Code |
| ML Ops Practitioner | The engineers who productionize ML systems; responsible for running, maintaining, and debugging ML pipelines (from ETL through deployment). Usually do not have a background in machine learning. | Visual Studio, VS Code, PyCharm (or other JetBrains tools) |
