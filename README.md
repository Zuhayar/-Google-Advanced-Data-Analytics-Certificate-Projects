
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "DtNBZFHO3M7n"
   },
   "source": [
    "# **Course 3 Automatidata project**\n",
    "**Course 3 - Go Beyond the Numbers: Translate Data into Insights**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "g-E8SNtmRUkN"
   },
   "source": [
    "You are the newest data professional in a fictional data consulting firm: Automatidata. The team is still early into the project, having only just completed an initial plan of action and some early Python coding work. \n",
    "\n",
    "Luana Rodriquez, the senior data analyst at Automatidata, is pleased with the work you have already completed and requests your assistance with some EDA and data visualization work for the New York City Taxi and Limousine Commission project (New York City TLC) to get a general understanding of what taxi ridership looks like. The management team is asking for a Python notebook showing data structuring and cleaning, as well as any matplotlib/seaborn visualizations plotted to help understand the data. At the very least, include a box plot of the ride durations and some time series plots, like a breakdown by quarter or month. \n",
    "\n",
    "Additionally, the management team has recently asked all EDA to include Tableau visualizations. For this taxi data, create a Tableau dashboard showing a New York City map of taxi/limo trips by month. Make sure it is easy to understand to someone who isn’t data savvy, and remember that the assistant director at the New York City TLC is a person with visual impairments.\n",
    "\n",
    "A notebook was structured and prepared to help you in this project. Please complete the following questions."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "rgSbVJvomcVa"
   },
   "source": [
    "# Course 3 End-of-course project: Exploratory data analysis\n",
    "\n",
    "In this activity, you will examine data provided and prepare it for analysis. You will also design a professional data visualization that tells a story, and will help data-driven decisions for business needs. \n",
    "\n",
    "Please note that the Tableau visualization activity is optional, and will not affect your completion of the course. Completing the Tableau activity will help you practice planning out and plotting a data visualization based on a specific business need. The structure of this activity is designed to emulate the proposals you will likely be assigned in your career as a data professional. Completing this activity will help prepare you for those career moments.\n",
    "\n",
    "**The purpose** of this project is to conduct exploratory data analysis on a provided data set. Your mission is to continue the investigation you began in C2 and perform further EDA on this data with the aim of learning more about the variables. \n",
    "  \n",
    "**The goal** is to clean data set and create a visualization.\n",
    "<br/>  \n",
    "*This activity has 4 parts:*\n",
    "\n",
    "**Part 1:** Imports, links, and loading\n",
    "\n",
    "**Part 2:** Data Exploration\n",
    "*   Data cleaning\n",
    "\n",
    "\n",
    "**Part 3:** Building visualizations\n",
    "\n",
    "**Part 4:** Evaluate and share results\n",
    "\n",
    "<br/> \n",
    "Follow the instructions and answer the questions below to complete the activity. Then, you will complete an Executive Summary using the questions listed on the PACE Strategy Document.\n",
    "\n",
    "Be sure to complete this activity before moving on. The next course item will provide you with a completed exemplar to compare to your own work. \n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "p5CHWd9rxIyp"
   },
   "source": [
    "# **Visualize a story in Tableau and Python**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "rdR5eWbYx8GE"
   },
   "source": [
    "# **PACE stages** \n",
    "\n",
    "\n",
    "<img src=\"images/Pace.png\" width=\"100\" height=\"100\" align=left>\n",
    "\n",
    "   *        [Plan](#scrollTo=psz51YkZVwtN&line=3&uniqifier=1)\n",
    "   *        [Analyze](#scrollTo=mA7Mz_SnI8km&line=4&uniqifier=1)\n",
    "   *        [Construct](#scrollTo=Lca9c8XON8lc&line=2&uniqifier=1)\n",
    "   *        [Execute](#scrollTo=401PgchTPr4E&line=2&uniqifier=1)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Throughout these project notebooks, you'll see references to the problem-solving framework PACE. The following notebook components are labeled with the respective PACE stage: Plan, Analyze, Construct, and Execute."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "xKLZJUqMx8GE"
   },
   "source": [
    "<img src=\"images/Plan.png\" width=\"100\" height=\"100\" align=left>\n",
    "\n",
    "\n",
    "## PACE: Plan \n",
    "\n",
    "In this stage, consider the following questions where applicable to complete your code response:\n",
    "1. Identify any outliers: \n",
    "\n",
    "\n",
    "*   What methods are best for identifying outliers?\n",
    "*   How do you make the decision to keep or exclude outliers from any future models?\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "What methods are best for identifying outliers?\n",
    "\n",
    "Use numpy functions to investigate the mean() and median() of the data and understand range of data values.\n",
    "Use a boxplot to visualize the distribution of the data.\n",
    "Use histograms to visualize the distribution of the data.\n",
    "\n",
    "How do you make the decision to keep or exclude outliers from any future models?\n",
    "\n",
    "There are three main options for dealing with outliers: keeping them as they are, deleting them, or reassigning them. Whether you keep outliers as they are, delete them, or reassign values is a decision that you make taking into account the nature of the outlying data and the assumptions of the model you are building. To help you make the decision, you can start with these general guidelines:\n",
    "\n",
    "Delete them: If you are sure the outliers are mistakes, typos, or errors and the dataset will be used for modeling or machine learning, then you are more likely to decide to delete outliers. Of the three choices, you’ll use this one the least.\n",
    "Reassign them: If the dataset is small and/or the data will be used for modeling or machine learning, you are more likely to choose a path of deriving new values to replace the outlier values.\n",
    "Leave them: For a dataset that you plan to do EDA/analysis on and nothing else, or for a dataset you are preparing for a model that is resistant to outliers, it is most likely that you are going to leave them in.\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "SKur6gTPRcvy"
   },
   "source": [
    "### Task 1. Imports, links, and loading\n",
    "Go to Tableau Public\n",
    "The following link will help you complete this activity. Keep Tableau Public open as you proceed to the next steps. \n",
    "\n",
    "Link to supporting materials: \n",
    "Tableau Public: https://public.tableau.com/s/ \n",
    "\n",
    "For EDA of the data, import the data and packages that would be most helpful, such as pandas, numpy and matplotlib. \n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {
    "id": "EO8vKZI8x8GF"
   },
   "outputs": [],
   "source": [
    "# Import packages and libraries\n",
    "#==> ENTER YOUR CODE HERE\n",
    "import pandas as pd\n",
    "import numpy as np\n",
    "import matplotlib.pyplot as plt\n",
    "import datetime as dt\n",
    "import seaborn as sns"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Note:** As shown in this cell, the dataset has been automatically loaded in for you. You do not need to download the .csv file, or provide more code, in order to access the dataset and proceed with this lab. Please continue with this activity by completing the following instructions."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {
    "id": "w7XSDxoqyF9D"
   },
   "outputs": [],
   "source": [
    "# Load dataset into dataframe\n",
    "df = pd.read_csv('2017_Yellow_Taxi_Trip_Data.csv')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "3mipEiyZx8GI"
   },
   "source": [
    "<img src=\"images/Analyze.png\" width=\"100\" height=\"100\" align=left>\n",
    "\n",
    "## PACE: Analyze \n",
    "\n",
    "Consider the questions in your PACE Strategy Document to reflect on the Analyze stage."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "n09krlKWRw_2"
   },
   "source": [
    "### Task 2a. Data exploration and cleaning\n",
    "\n",
    "Decide which columns are applicable\n",
    "\n",
    "The first step is to assess your data. Check the Data Source page on Tableau Public to get a sense of the size, shape and makeup of the data set. Then answer these questions to yourself: \n",
    "\n",
    "Given our scenario, which data columns are most applicable? \n",
    "Which data columns can I eliminate, knowing they won’t solve our problem scenario? \n",
    "\n",
    "Consider functions that help you understand and structure the data. \n",
    "\n",
    "*    head()\n",
    "*    describe()\n",
    "*    info()\n",
    "*    groupby()\n",
    "*    sortby()\n",
    "\n",
    "What do you do about missing data (if any)? \n",
    "\n",
    "Are there data outliers? What are they and how might you handle them? \n",
    "\n",
    "What do the distributions of your variables tell you about the question you're asking or the problem you're trying to solve?\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "==> ENTER YOUR RESPONSE HERE"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "uk6zuv_mUU2k"
   },
   "source": [
    "Start by discovering, using head and size. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {
    "id": "cBOUo5p-tbib"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Unnamed: 0</th>\n",
       "      <th>VendorID</th>\n",
       "      <th>tpep_pickup_datetime</th>\n",
       "      <th>tpep_dropoff_datetime</th>\n",
       "      <th>passenger_count</th>\n",
       "      <th>trip_distance</th>\n",
       "      <th>RatecodeID</th>\n",
       "      <th>store_and_fwd_flag</th>\n",
       "      <th>PULocationID</th>\n",
       "      <th>DOLocationID</th>\n",
       "      <th>payment_type</th>\n",
       "      <th>fare_amount</th>\n",
       "      <th>extra</th>\n",
       "      <th>mta_tax</th>\n",
       "      <th>tip_amount</th>\n",
       "      <th>tolls_amount</th>\n",
       "      <th>improvement_surcharge</th>\n",
       "      <th>total_amount</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>24870114</td>\n",
       "      <td>2</td>\n",
       "      <td>03/25/2017 8:55:43 AM</td>\n",
       "      <td>03/25/2017 9:09:47 AM</td>\n",
       "      <td>6</td>\n",
       "      <td>3.34</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>100</td>\n",
       "      <td>231</td>\n",
       "      <td>1</td>\n",
       "      <td>13.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>2.76</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>16.56</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>35634249</td>\n",
       "      <td>1</td>\n",
       "      <td>04/11/2017 2:53:28 PM</td>\n",
       "      <td>04/11/2017 3:19:58 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>1.80</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>186</td>\n",
       "      <td>43</td>\n",
       "      <td>1</td>\n",
       "      <td>16.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>4.00</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>20.80</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>106203690</td>\n",
       "      <td>1</td>\n",
       "      <td>12/15/2017 7:26:56 AM</td>\n",
       "      <td>12/15/2017 7:34:08 AM</td>\n",
       "      <td>1</td>\n",
       "      <td>1.00</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>262</td>\n",
       "      <td>236</td>\n",
       "      <td>1</td>\n",
       "      <td>6.5</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>1.45</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>8.75</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>38942136</td>\n",
       "      <td>2</td>\n",
       "      <td>05/07/2017 1:17:59 PM</td>\n",
       "      <td>05/07/2017 1:48:14 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>3.70</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>188</td>\n",
       "      <td>97</td>\n",
       "      <td>1</td>\n",
       "      <td>20.5</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>6.39</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>27.69</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>30841670</td>\n",
       "      <td>2</td>\n",
       "      <td>04/15/2017 11:32:20 PM</td>\n",
       "      <td>04/15/2017 11:49:03 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>4.37</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>4</td>\n",
       "      <td>112</td>\n",
       "      <td>2</td>\n",
       "      <td>16.5</td>\n",
       "      <td>0.5</td>\n",
       "      <td>0.5</td>\n",
       "      <td>0.00</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>17.80</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   Unnamed: 0  VendorID    tpep_pickup_datetime   tpep_dropoff_datetime  \\\n",
       "0    24870114         2   03/25/2017 8:55:43 AM   03/25/2017 9:09:47 AM   \n",
       "1    35634249         1   04/11/2017 2:53:28 PM   04/11/2017 3:19:58 PM   \n",
       "2   106203690         1   12/15/2017 7:26:56 AM   12/15/2017 7:34:08 AM   \n",
       "3    38942136         2   05/07/2017 1:17:59 PM   05/07/2017 1:48:14 PM   \n",
       "4    30841670         2  04/15/2017 11:32:20 PM  04/15/2017 11:49:03 PM   \n",
       "\n",
       "   passenger_count  trip_distance  RatecodeID store_and_fwd_flag  \\\n",
       "0                6           3.34           1                  N   \n",
       "1                1           1.80           1                  N   \n",
       "2                1           1.00           1                  N   \n",
       "3                1           3.70           1                  N   \n",
       "4                1           4.37           1                  N   \n",
       "\n",
       "   PULocationID  DOLocationID  payment_type  fare_amount  extra  mta_tax  \\\n",
       "0           100           231             1         13.0    0.0      0.5   \n",
       "1           186            43             1         16.0    0.0      0.5   \n",
       "2           262           236             1          6.5    0.0      0.5   \n",
       "3           188            97             1         20.5    0.0      0.5   \n",
       "4             4           112             2         16.5    0.5      0.5   \n",
       "\n",
       "   tip_amount  tolls_amount  improvement_surcharge  total_amount  \n",
       "0        2.76           0.0                    0.3         16.56  \n",
       "1        4.00           0.0                    0.3         20.80  \n",
       "2        1.45           0.0                    0.3          8.75  \n",
       "3        6.39           0.0                    0.3         27.69  \n",
       "4        0.00           0.0                    0.3         17.80  "
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#==> ENTER YOUR CODE HERE\n",
    "df.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {
    "id": "GvT82D1qyF9F"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "408582"
      ]
     },
     "execution_count": 6,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#==> ENTER YOUR CODE HERE\n",
    "df.size"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "WulP4lZ9UVgy"
   },
   "source": [
    "Use describe... "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {
    "id": "xMpkdNQ0UPmW"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Unnamed: 0</th>\n",
       "      <th>VendorID</th>\n",
       "      <th>passenger_count</th>\n",
       "      <th>trip_distance</th>\n",
       "      <th>RatecodeID</th>\n",
       "      <th>PULocationID</th>\n",
       "      <th>DOLocationID</th>\n",
       "      <th>payment_type</th>\n",
       "      <th>fare_amount</th>\n",
       "      <th>extra</th>\n",
       "      <th>mta_tax</th>\n",
       "      <th>tip_amount</th>\n",
       "      <th>tolls_amount</th>\n",
       "      <th>improvement_surcharge</th>\n",
       "      <th>total_amount</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>count</th>\n",
       "      <td>2.269900e+04</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "      <td>22699.000000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>mean</th>\n",
       "      <td>5.675849e+07</td>\n",
       "      <td>1.556236</td>\n",
       "      <td>1.642319</td>\n",
       "      <td>2.913313</td>\n",
       "      <td>1.043394</td>\n",
       "      <td>162.412353</td>\n",
       "      <td>161.527997</td>\n",
       "      <td>1.336887</td>\n",
       "      <td>13.026629</td>\n",
       "      <td>0.333275</td>\n",
       "      <td>0.497445</td>\n",
       "      <td>1.835781</td>\n",
       "      <td>0.312542</td>\n",
       "      <td>0.299551</td>\n",
       "      <td>16.310502</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>std</th>\n",
       "      <td>3.274493e+07</td>\n",
       "      <td>0.496838</td>\n",
       "      <td>1.285231</td>\n",
       "      <td>3.653171</td>\n",
       "      <td>0.708391</td>\n",
       "      <td>66.633373</td>\n",
       "      <td>70.139691</td>\n",
       "      <td>0.496211</td>\n",
       "      <td>13.243791</td>\n",
       "      <td>0.463097</td>\n",
       "      <td>0.039465</td>\n",
       "      <td>2.800626</td>\n",
       "      <td>1.399212</td>\n",
       "      <td>0.015673</td>\n",
       "      <td>16.097295</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>min</th>\n",
       "      <td>1.212700e+04</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>-120.000000</td>\n",
       "      <td>-1.000000</td>\n",
       "      <td>-0.500000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>-0.300000</td>\n",
       "      <td>-120.300000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>25%</th>\n",
       "      <td>2.852056e+07</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>0.990000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>114.000000</td>\n",
       "      <td>112.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>6.500000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.500000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.300000</td>\n",
       "      <td>8.750000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50%</th>\n",
       "      <td>5.673150e+07</td>\n",
       "      <td>2.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>1.610000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>162.000000</td>\n",
       "      <td>162.000000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>9.500000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.500000</td>\n",
       "      <td>1.350000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.300000</td>\n",
       "      <td>11.800000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>75%</th>\n",
       "      <td>8.537452e+07</td>\n",
       "      <td>2.000000</td>\n",
       "      <td>2.000000</td>\n",
       "      <td>3.060000</td>\n",
       "      <td>1.000000</td>\n",
       "      <td>233.000000</td>\n",
       "      <td>233.000000</td>\n",
       "      <td>2.000000</td>\n",
       "      <td>14.500000</td>\n",
       "      <td>0.500000</td>\n",
       "      <td>0.500000</td>\n",
       "      <td>2.450000</td>\n",
       "      <td>0.000000</td>\n",
       "      <td>0.300000</td>\n",
       "      <td>17.800000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>max</th>\n",
       "      <td>1.134863e+08</td>\n",
       "      <td>2.000000</td>\n",
       "      <td>6.000000</td>\n",
       "      <td>33.960000</td>\n",
       "      <td>99.000000</td>\n",
       "      <td>265.000000</td>\n",
       "      <td>265.000000</td>\n",
       "      <td>4.000000</td>\n",
       "      <td>999.990000</td>\n",
       "      <td>4.500000</td>\n",
       "      <td>0.500000</td>\n",
       "      <td>200.000000</td>\n",
       "      <td>19.100000</td>\n",
       "      <td>0.300000</td>\n",
       "      <td>1200.290000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "         Unnamed: 0      VendorID  passenger_count  trip_distance  \\\n",
       "count  2.269900e+04  22699.000000     22699.000000   22699.000000   \n",
       "mean   5.675849e+07      1.556236         1.642319       2.913313   \n",
       "std    3.274493e+07      0.496838         1.285231       3.653171   \n",
       "min    1.212700e+04      1.000000         0.000000       0.000000   \n",
       "25%    2.852056e+07      1.000000         1.000000       0.990000   \n",
       "50%    5.673150e+07      2.000000         1.000000       1.610000   \n",
       "75%    8.537452e+07      2.000000         2.000000       3.060000   \n",
       "max    1.134863e+08      2.000000         6.000000      33.960000   \n",
       "\n",
       "         RatecodeID  PULocationID  DOLocationID  payment_type   fare_amount  \\\n",
       "count  22699.000000  22699.000000  22699.000000  22699.000000  22699.000000   \n",
       "mean       1.043394    162.412353    161.527997      1.336887     13.026629   \n",
       "std        0.708391     66.633373     70.139691      0.496211     13.243791   \n",
       "min        1.000000      1.000000      1.000000      1.000000   -120.000000   \n",
       "25%        1.000000    114.000000    112.000000      1.000000      6.500000   \n",
       "50%        1.000000    162.000000    162.000000      1.000000      9.500000   \n",
       "75%        1.000000    233.000000    233.000000      2.000000     14.500000   \n",
       "max       99.000000    265.000000    265.000000      4.000000    999.990000   \n",
       "\n",
       "              extra       mta_tax    tip_amount  tolls_amount  \\\n",
       "count  22699.000000  22699.000000  22699.000000  22699.000000   \n",
       "mean       0.333275      0.497445      1.835781      0.312542   \n",
       "std        0.463097      0.039465      2.800626      1.399212   \n",
       "min       -1.000000     -0.500000      0.000000      0.000000   \n",
       "25%        0.000000      0.500000      0.000000      0.000000   \n",
       "50%        0.000000      0.500000      1.350000      0.000000   \n",
       "75%        0.500000      0.500000      2.450000      0.000000   \n",
       "max        4.500000      0.500000    200.000000     19.100000   \n",
       "\n",
       "       improvement_surcharge  total_amount  \n",
       "count           22699.000000  22699.000000  \n",
       "mean                0.299551     16.310502  \n",
       "std                 0.015673     16.097295  \n",
       "min                -0.300000   -120.300000  \n",
       "25%                 0.300000      8.750000  \n",
       "50%                 0.300000     11.800000  \n",
       "75%                 0.300000     17.800000  \n",
       "max                 0.300000   1200.290000  "
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#==> ENTER YOUR CODE HERE\n",
    "df.describe()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "psmn0VD0UWBk"
   },
   "source": [
    "And info. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {
    "id": "Thlb8oiyUPwe"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 22699 entries, 0 to 22698\n",
      "Data columns (total 18 columns):\n",
      " #   Column                 Non-Null Count  Dtype  \n",
      "---  ------                 --------------  -----  \n",
      " 0   Unnamed: 0             22699 non-null  int64  \n",
      " 1   VendorID               22699 non-null  int64  \n",
      " 2   tpep_pickup_datetime   22699 non-null  object \n",
      " 3   tpep_dropoff_datetime  22699 non-null  object \n",
      " 4   passenger_count        22699 non-null  int64  \n",
      " 5   trip_distance          22699 non-null  float64\n",
      " 6   RatecodeID             22699 non-null  int64  \n",
      " 7   store_and_fwd_flag     22699 non-null  object \n",
      " 8   PULocationID           22699 non-null  int64  \n",
      " 9   DOLocationID           22699 non-null  int64  \n",
      " 10  payment_type           22699 non-null  int64  \n",
      " 11  fare_amount            22699 non-null  float64\n",
      " 12  extra                  22699 non-null  float64\n",
      " 13  mta_tax                22699 non-null  float64\n",
      " 14  tip_amount             22699 non-null  float64\n",
      " 15  tolls_amount           22699 non-null  float64\n",
      " 16  improvement_surcharge  22699 non-null  float64\n",
      " 17  total_amount           22699 non-null  float64\n",
      "dtypes: float64(8), int64(7), object(3)\n",
      "memory usage: 3.1+ MB\n"
     ]
    }
   ],
   "source": [
    "#==> ENTER YOUR CODE HERE\n",
    "df.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "vCGi3U9nw4Er"
   },
   "source": [
    "### Task 2b. Assess whether dimensions and measures are correct"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "aNBRa33TR_Is"
   },
   "source": [
    "On the data source page in Tableau, double check the data types for the applicable columns you selected on the previous step. Pay close attention to the dimensions and measures to assure they are correct. \n",
    "\n",
    "In Python, consider the data types of the columns. *Consider:* Do they make sense? "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "ywUoKjQRyF9I"
   },
   "source": [
    "Review the link provided in the previous activity instructions to create the required Tableau visualization. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "sPlm615Ywifi"
   },
   "source": [
    "### Task 2c. Select visualization type(s)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "2YdC51QBSG2v"
   },
   "source": [
    "Select data visualization types that will help you understand and explain the data.\n",
    "\n",
    "Now that you know which data columns you’ll use, it is time to decide which data visualization makes the most sense for EDA of the TLC dataset. What type of data visualization(s) would be most helpful? \n",
    "\n",
    "* Line graph\n",
    "* Bar chart\n",
    "* Box plot\n",
    "* Histogram\n",
    "* Heat map\n",
    "* Scatter plot\n",
    "* A geographic map\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "oYuUVTY-cD3y"
   },
   "source": [
    "As you'll see below, a bar chart, box plot and scatter plot will be most helpful in your understanding of this data.\n",
    "\n",
    "A box plot will be helpful to determine outliers and where the bulk of the data points reside in terms of trip_distance, duration, and total_amount\n",
    "\n",
    "A scatter plot will be helpful to visualize the trends and patters and outliers of critical variables, such as trip_distance and total_amount\n",
    "\n",
    "A bar chart will help determine average number of trips per month, weekday, weekend, etc."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "f0sHpfkhx8GM"
   },
   "source": [
    "<img src=\"images/Construct.png\" width=\"100\" height=\"100\" align=left>\n",
    "\n",
    "## PACE: Construct \n",
    "\n",
    "Consider the questions in your PACE Strategy Document to reflect on the Construct stage."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "BYWkZ4i3wgv4"
   },
   "source": [
    "### Task 3. Data visualization\n",
    "\n",
    "You’ve assessed your data, and decided on which data variables are most applicable. It’s time to plot your visualization(s)!\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "oMOs4lb1crry"
   },
   "source": [
    "### Boxplots"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Perform a check for outliers on relevant columns such as trip distance and trip duration. Remember, some of the best ways to identify the presence of outliers in data are box plots and histograms. \n",
    "\n",
    "**Note:** Remember to convert your date columns to datetime in order to derive total trip duration.  "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {
    "id": "9K6Alb7uc9my"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7ff0205f0c50>"
      ]
     },
     "execution_count": 9,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 504x144 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Convert data columns to datetime\n",
    "df['tpep_dropoff_datetimepep'] = pd.to_datetime(df['tpep_dropoff_datetime'])\n",
    "df['tpep_pickup_datetime'] = pd.to_datetime(df['tpep_pickup_datetime'])\n",
    "#==> ENTER YOUR CODE HERE\n",
    "\n",
    "plt.figure(figsize=(7,2))\n",
    "plt.title('trip distance')\n",
    "sns.boxplot(data=None,x=df['trip_distance'],fliersize=1)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**trip distance**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7fef5b67a290>"
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create box plot of trip_distance\n",
    "plt.title('trip distance')\n",
    "#==> ENTER YOUR CODE HERE\n",
    "sns.boxplot(data=None,x=df['trip_distance'],fliersize=1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7fef5b59ba10>"
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 720x360 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create histogram of trip_distance\n",
    "\n",
    "#==> ENTER YOUR CODE HERE\n",
    "plt.figure(figsize=(10,5))\n",
    "sns.histplot(x=df['trip_distance'],bins=range(0,26,1))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**total amount**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 12,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7fef5b5fb990>"
      ]
     },
     "execution_count": 12,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 504x144 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create box plot of total_amount\n",
    "plt.figure(figsize=(7,2))\n",
    "plt.title('total amount')\n",
    "sns.boxplot(data=None,x=df['total_amount'],fliersize=1)\n",
    "#==> ENTER YOUR CODE HERE"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 13,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Total amount Histogram')"
      ]
     },
     "execution_count": 13,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 720x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create histogram of total_amount\n",
    "plt.figure(figsize=(10,6))\n",
    "#==> ENTER YOUR CODE HERE\n",
    "ax = sns.histplot(x=df['total_amount'],bins=range(-10,101,1))\n",
    "ax.set_xticks(range(-10,101,5))\n",
    "ax.set_xticklabels(range(-10,101,5))\n",
    "plt.title('Total amount Histogram')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**tip amount**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 14,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7fef5b46d550>"
      ]
     },
     "execution_count": 14,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 720x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create box plot of tip_amount\n",
    "#==> ENTER YOUR CODE HERE\n",
    "plt.figure(figsize=(10,6))\n",
    "plt.title('Tip Amount')\n",
    "sns.boxplot(data=None,x=df['tip_amount'],fliersize=1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 15,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create histogram of tip_amount\n",
    "#==> ENTER YOUR CODE HERE\n",
    "sns.histplot(x=df['tip_amount'],bins=range(0,21,1))\n",
    "ax.set_xticks(range(0,21,1))\n",
    "ax.set_xticklabels(range(0,21,1))\n",
    "plt.title('Tip amount histogram');"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**tip_amount by vendor**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Tip amount by vendor histogram')"
      ]
     },
     "execution_count": 16,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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7rzzTu6//36e9axnMXv2bI466ih+8YtfAL2jzqeeeiqzZ8/maU97GjfffDMAy5cv50UvehH77rsvf/Znf0ZVPVzjjDPOYJ999mGfffbhzDPPfLjOnnvuyete9zpmz57NkiVL1tjHHXfckbPPPpv3ve99v7PdR8ugLUmSpOa233579t9/fy655BKgdzT70EMP5fTTT+dLX/oS11xzDXPmzOGMM854eJ0ddtiBa665hhNPPJF3vetdAJx22mkcdNBBXHvttRx22GEsXrwYgKuvvpoPfehDXHnllXzzm9/k3//937n22msBuOWWWzjmmGO49tpr2W233dbazyc96Uk89NBD3HPPPY95nw3akiRJGoj+4SMLFixg991358Ybb+TZz342s2bNYv78+dxxxx0PL3/kkUcCsN9++7Fo0SIAvvKVr/CqV70KgJe+9KVsu+22AHzta1/jZS97GVtssQVbbrklRx55JF/96lcB2G233TjggANG3c+xOJoN3rBGkiRJA3LEEUdw8sknc8011/CrX/2Kfffdlxe+8IWcf/75Iy6/6aabAr0TFleuXPlw+0iX2ltbON5iiy1G3ccf/OAHTJo0iR133HHU66yJR7QlSZI0EFtuuSWHHHIIr3nNa5g3bx4HHHAAX//617ntttsAuP/++/ne97631m0cfPDBfOQjHwHg4osv5ic/+cnD7Z/5zGe4//77+eUvf8mnP/1pnvOc56xX/5YtW8af//mfc9JJJ43JNcA9oi1JkqSBmTdvHkceeSQLFixg2rRpnHPOOcybN+/hkyTf/va385SnPGWN65966qnMmzeP2bNn89znPpddd90VgNmzZ3Pcccex//77A/Da176Wfffd9+EhJ2vyq1/9ilmzZrFixQomT57Mq1/9ak4++eQx2deM1RiU8WbOnDm1cOHCgdfddbeZLFl8x7oXbGDGrrux+I5FQ6ktSZLU76abbmLPPfccdjfG1Ej7lOTqqpoz0vIe0R5jSxbfwSU33j+U2nP32nwodSVJkvRIjtGWJEmSGjBoS5IkSQ0YtCVJkqQGDNqSJElSAwZtSZIkqQGDtiRJkoZi191mkmTMHrvuNnOdNV/zmtew4447ss8++zTfPy/vJ0mSpKEY68sij+ZSx8cddxwnnXQSxxxzzJjVXROPaEuSJGmjcfDBB7PddtsNpJZBW5IkSWrAoC1JkiQ1YNCWJEmSGjBoS5IkSQ141RFJkiQNxYxddxvVlULWZ3vrMm/ePC6//HLuvfdepk+fzmmnncbxxx8/Zn3oZ9CWJEnSUCy+Y9HAa55//vkDq+XQEUmSJKkBg7YkSZLUgEFbkiRJasCgLUmSJDVg0JYkSZIaaBq0k/xlkhuSfDfJ+UmmJtkuyaVJbu2et+1b/pQktyW5JcmL+9r3S3J9N++9SdKy35IkSdJj1SxoJ9kFeAMwp6r2ASYBRwNvAS6rqj2Ay7rXJNmrm783MBd4f5JJ3ebOAk4A9ugec1v1W5IkSYMxc9cZJBmzx8xdZ6yz5pIlS3je857Hnnvuyd5778173vOeZvvX+jrak4HNkqwANgfuBE4BDunmzwcuB/4WOBxYUFUPALcnuQ3YP8kiYOuqugIgybnAEcDFjfsuSZKkhu5YspT6xvwx214OPHady0yePJl3v/vdzJ49m/vuu4/99tuPF77whey1115j1o9Vmh3RrqofAu8CFgN3AT+rqi8CO1XVXd0ydwE7dqvsAizp28TSrm2Xbnr19kdIckKShUkWLlu2bCx3R5IkSRuAnXfemdmzZwOw1VZbseeee/LDH/6wSa2WQ0e2pXeUenfgicAWSV61tlVGaKu1tD+ysersqppTVXOmTZu2vl2WJEnSRmTRokVce+21PPOZz2yy/ZYnQ74AuL2qllXVCuBTwIHA3Ul2Buie7+mWXwr0D6yZTm+oydJuevV2SZIk6VH5xS9+wctf/nLOPPNMtt566yY1WgbtxcABSTbvrhJyKHATcBGwagDNscCF3fRFwNFJNk2yO72THq/qhpfcl+SAbjvH9K0jSZIkrZcVK1bw8pe/nFe+8pUceeSRzeo0Oxmyqq5M8gngGmAlcC1wNrAlcEGS4+mF8aO65W9IcgFwY7f866vqwW5zJwLnAJvROwnSEyElSZK03qqK448/nj333JOTTz65aa2mVx2pqlOBU1drfoDe0e2Rlj8dOH2E9oXAPmPeQUmSJA3NbjOmj+pKIeuzvXX5+te/znnnncfTnvY0Zs2aBcA73vEOXvKSl4xZP1ZpfXk/SZIkaUSLFi9Z90Jj7KCDDqJqxOtqjDlvwS5JkiQ1YNCWJEmSGjBoS5IkqYlBDdEYhEezLwZtSZIkjbmpU6eyfPnyDSJsVxXLly9n6tSp67WeJ0NKkiRpzE2fPp2lS5eybNmyYXdlTEydOpXp09d9VZN+Bm1JkiSNuSlTprD77rsPuxtD5dARSZIkqQGDtiRJktSAQVuSJElqwKAtSZIkNWDQliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgMGbUmSJKkBg7YkSZLUgEFbkiRJasCgLUmSJDVg0JYkSZIaMGhLkiRJDRi0JUmSpAYM2pIkSVIDBm1JkiSpAYO2JEmS1IBBW5IkSWrAoC1JkiQ1YNCWJEmSGjBoS5IkSQ0YtCVJkqQGDNqSJElSAwZtSZIkqQGDtiRJktRAs6Cd5KlJrut7/DzJm5Jsl+TSJLd2z9v2rXNKktuS3JLkxX3t+yW5vpv33iRp1W9JkiRpLDQL2lV1S1XNqqpZwH7A/cCngbcAl1XVHsBl3WuS7AUcDewNzAXen2RSt7mzgBOAPbrH3Fb9liRJksbCoIaOHAp8v6ruAA4H5nft84EjuunDgQVV9UBV3Q7cBuyfZGdg66q6oqoKOLdvHUmSJGlcGlTQPho4v5veqaruAuied+zadwGW9K2ztGvbpZtevf0RkpyQZGGShcuWLRvD7kuSJEnrp3nQTrIJcBjw8XUtOkJbraX9kY1VZ1fVnKqaM23atPXrqCRJkjSGBnFE+/eBa6rq7u713d1wELrne7r2pcCMvvWmA3d27dNHaJckSZLGrUEE7Xn8dtgIwEXAsd30scCFfe1HJ9k0ye70Tnq8qhtecl+SA7qrjRzTt44kSZI0Lk1uufEkmwMvBP6sr/mdwAVJjgcWA0cBVNUNSS4AbgRWAq+vqge7dU4EzgE2Ay7uHpIkSdK41TRoV9X9wPartS2ndxWSkZY/HTh9hPaFwD4t+ihJkiS14J0hJUmSpAYM2pIkSVIDBm1JkiSpAYO2JEmS1IBBW5IkSWrAoC1JkiQ1YNCWJEmSGjBoS5IkSQ0YtCVJkqQGDNqSJElSAwZtSZIkqQGDtiRJktSAQVuSJElqwKAtSZIkNWDQliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgMGbUmSJKkBg7YkSZLUgEFbkiRJasCgLUmSJDVg0JYkSZIaMGhLkiRJDRi0JUmSpAYM2pIkSVIDBm1JkiSpAYO2JEmS1IBBW5IkSWrAoC1JkiQ1YNCWJEmSGjBoS5IkSQ0YtDcgkyZPIcnAH7vuNnPYuy5JkjTuTB52BzR2Hly5gktuvH/gdefutfnAa0qSJI13TY9oJ9kmySeS3JzkpiTPSrJdkkuT3No9b9u3/ClJbktyS5IX97Xvl+T6bt57k6RlvyVJkqTHqvXQkfcAl1TV/wSeDtwEvAW4rKr2AC7rXpNkL+BoYG9gLvD+JJO67ZwFnADs0T3mNu63JEmS9Jg0C9pJtgYOBv4DoKp+U1U/BQ4H5neLzQeO6KYPBxZU1QNVdTtwG7B/kp2Bravqiqoq4Ny+dSRJkqRxqeUR7ScBy4APJbk2yQeSbAHsVFV3AXTPO3bL7wIs6Vt/ade2Sze9evsjJDkhycIkC5ctWza2eyNJkiSth5ZBezIwGzirqvYFfkk3TGQNRhp3XWtpf2Rj1dlVNaeq5kybNm19+ytJkiSNmZZBeymwtKqu7F5/gl7wvrsbDkL3fE/f8jP61p8O3Nm1Tx+hXZIkSRq3mgXtqvoRsCTJU7umQ4EbgYuAY7u2Y4ELu+mLgKOTbJpkd3onPV7VDS+5L8kB3dVGjulbR5IkSRqXWl9H+y+AjyTZBPgB8Cf0wv0FSY4HFgNHAVTVDUkuoBfGVwKvr6oHu+2cCJwDbAZc3D0kSZKkcatp0K6q64A5I8w6dA3Lnw6cPkL7QmCfse2dJEmS1I63YJckSZIaMGhLkiRJDRi0JUmSpAYM2pIkSVIDBm1JkiSpAYO2JEmS1IBBW5IkSWrAoC1JkiQ1YNCWJEmSGjBoS5IkSQ0YtCVJkqQGDNqSJElSAwZtSZIkqQGDtiRJktSAQVuSJElqwKAtSZIkNWDQliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgMGbUmSJKkBg7YkSZLUgEFbkiRJasCgLUmSJDVg0JYkSZIaMGhLkiRJDRi0JUmSpAYM2pIkSVIDBm1JkiSpAYO2JEmS1IBBW5IkSWrAoC1JkiQ1YNCWJEmSGmgatJMsSnJ9kuuSLOzatktyaZJbu+dt+5Y/JcltSW5J8uK+9v267dyW5L1J0rLfkiRJ0mM1iCPaz6uqWVU1p3v9FuCyqtoDuKx7TZK9gKOBvYG5wPuTTOrWOQs4Adije8wdQL8lSZKkR20YQ0cOB+Z30/OBI/raF1TVA1V1O3AbsH+SnYGtq+qKqirg3L51JEmSpHGpddAu4ItJrk5yQte2U1XdBdA979i17wIs6Vt3ade2Sze9evsjJDkhycIkC5ctWzaGuyFJkiStn8mNt//sqrozyY7ApUluXsuyI427rrW0P7Kx6mzgbIA5c+aMuIwkSZI0CE2PaFfVnd3zPcCngf2Bu7vhIHTP93SLLwVm9K0+Hbiza58+QrskSZI0bjUL2km2SLLVqmngRcB3gYuAY7vFjgUu7KYvAo5OsmmS3emd9HhVN7zkviQHdFcbOaZvHUmSJGlcajl0ZCfg092V+CYDH62qS5J8C7ggyfHAYuAogKq6IckFwI3ASuD1VfVgt60TgXOAzYCLu4ckSZI0bjUL2lX1A+DpI7QvBw5dwzqnA6eP0L4Q2Ges+9jCJptOZe5emw+7G5IkSRqy1idDbnR+88CvqW/MX/eCDeTAY9e9kCRJkgbCW7BLkiRJDRi0JUmSpAZGFbSTPHs0bZIkSZJ6RntE+/+Msk2SJEkS6zgZMsmzgAOBaUlO7pu1NTCpZcckSZKkiWxdVx3ZBNiyW26rvvafA69o1SlJkiRpoltr0K6qLwNfTnJOVd0xoD5JkiRJE95or6O9aZKzgZn961TV81t0SpIkSZroRhu0Pw78G/AB4MF1LCtJkiRt9EYbtFdW1VlNeyJJkiRtQEZ7eb/PJnldkp2TbLfq0bRnkiRJ0gQ22iPax3bPb+5rK+BJY9sdSZIkacMwqqBdVbu37ogkSZK0IRlV0E5yzEjtVXXu2HZHkiRJ2jCMdujIM/qmpwKHAtcABm1JkiRpBKMdOvIX/a+TPB44r0mPJEmSpA3AaK86srr7gT3GsiOSJEnShmS0Y7Q/S+8qIwCTgD2BC1p1SpIkSZroRjtG+1190yuBO6pqaYP+SJIkSRuEUQ0dqaovAzcDWwHbAr9p2SlJkiRpohtV0E7yh8BVwFHAHwJXJnlFy45JkiRJE9loh468FXhGVd0DkGQa8CXgE606JkmSJE1ko73qyONWhezO8vVYV5IkSdrojPaI9iVJvgCc373+I+DzbbokSZIkTXxrDdpJ/gewU1W9OcmRwEFAgCuAjwygf5IkSdKEtK7hH2cC9wFU1aeq6uSq+kt6R7PPbN05SZIkaaJaV9CeWVXfWb2xqhYCM5v0SJIkSdoArCtoT13LvM3GsiOSJEnShmRdQftbSf509cYkxwNXt+mSJEmSNPGt66ojbwI+neSV/DZYzwE2AV7WsmOSJEnSRLbWoF1VdwMHJnkesE/X/J9V9V/NeyZJkiRNYKO6jnZV/Tfw3437IkmSJG0wmt/dMcmkJNcm+Vz3ersklya5tXvetm/ZU5LcluSWJC/ua98vyfXdvPcmSet+S5IkSY/FIG6j/kbgpr7XbwEuq6o9gMu61yTZCzga2BuYC7w/yaRunbOAE4A9usfcAfRbkiRJetSaBu0k04GXAh/oaz4cmN9NzweO6GtfUFUPVNXtwG3A/kl2BrauqiuqqoBz+9aRJEmSxqXWR7TPBP4GeKivbaequguge96xa98FWNK33NKubZduevX2R0hyQpKFSRYuW7ZsbPZAkiRJehSaBe0kfwDcU1Wjvd72SOOuay3tj2ysOruq5lTVnGnTpo2yrCRJkjT2RnXVkUfp2cBhSV5C7w6TWyf5MHB3kp2r6q5uWMg93fJLgRl9608H7uzap4/QrnFi0uQpDOP81Bm77sbiOxYNvK4kSdJoNAvaVXUKcApAkkOAv66qVyX5V+BY4J3d84XdKhcBH01yBvBEeic9XlVVDya5L8kBwJXAMcD/adVvrb8HV67gkhvvH3jduXttPvCakiRJo9XyiPaavBO4oLuN+2LgKICquiHJBcCNwErg9VX1YLfOicA5wGbAxd1DkiRJGrcGErSr6nLg8m56OXDoGpY7HTh9hPaF/PbOlJIkSdK4N4jraEuSJEkbHYO2JEmS1IBBW5IkSWrAoC1JkiQ1YNCWJEmSGjBoS5IkSQ0YtCVJkqQGDNqSJElSAwZtSZIkqQGDtiRJktSAQVuSJElqwKAtSZIkNWDQliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgMGbUmSJKkBg7YkSZLUgEFbkiRJasCgLUmSJDVg0JYkSZIaMGhLkiRJDRi0JUmSpAYmD7sDGjuTp0xh7l6bD7sbkiRJwqC9QVm5YgX1jfkDr5sDjx14TUmSpPHOoSOSJElSAwZtSZIkqQGDtiRJktSAQVuSJElqwKAtSZIkNWDQliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgPNgnaSqUmuSvLtJDckOa1r3y7JpUlu7Z637VvnlCS3JbklyYv72vdLcn03771J0qrfkiRJ0lhoeUT7AeD5VfV0YBYwN8kBwFuAy6pqD+Cy7jVJ9gKOBvYG5gLvTzKp29ZZwAnAHt1jbsN+S5IkSY9Zs6BdPb/oXk7pHgUcDszv2ucDR3TThwMLquqBqroduA3YP8nOwNZVdUVVFXBu3zqSJEnSuNR0jHaSSUmuA+4BLq2qK4GdquougO55x27xXYAlfasv7dp26aZXbx+p3glJFiZZuGzZsrHdGUmSJGk9NA3aVfVgVc0CptM7Or3PWhYfadx1raV9pHpnV9Wcqpozbdq09e+wJEmSNEYGctWRqvopcDm9sdV3d8NB6J7v6RZbCszoW206cGfXPn2EdkmSJGncannVkWlJtummNwNeANwMXAQc2y12LHBhN30RcHSSTZPsTu+kx6u64SX3JTmgu9rIMX3rSJIkSePS5Ibb3hmY31055HHABVX1uSRXABckOazNoPkAABMWSURBVB5YDBwFUFU3JLkAuBFYCby+qh7stnUicA6wGXBx95AkSZLGrWZBu6q+A+w7Qvty4NA1rHM6cPoI7QuBtY3vliRJksYV7wwpSZIkNWDQliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgMGbUmSJKkBg7YkSZLUgEFbkiRJasCgLUmSJDVg0JYkSZIaMGhLkiRJDRi0JUmSpAYM2pIkSVIDBm1JkiSpAYO2JEmS1IBBW5IkSWrAoC1JkiQ1YNCWJEmSGjBoS5IkSQ0YtCVJkqQGDNqSJElSAwZtSZIkqQGDtiRJktSAQVuSJElqwKAtSZIkNWDQliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgOTh90BTXyTp0xh7l6bD7zuJptOHXhNSZKk0TJo6zFbuWIF9Y35A6+bA48deE1JkqTRcuiIJEmS1IBBW5IkSWqgWdBOMiPJfye5KckNSd7YtW+X5NIkt3bP2/atc0qS25LckuTFfe37Jbm+m/feJGnVb0mSJGkstDyivRL4q6raEzgAeH2SvYC3AJdV1R7AZd1runlHA3sDc4H3J5nUbess4ARgj+4xt2G/JUmSpMesWdCuqruq6ppu+j7gJmAX4HBg1Zlz84EjuunDgQVV9UBV3Q7cBuyfZGdg66q6oqoKOLdvHUmSJGlcGsgY7SQzgX2BK4Gdquou6IVxYMdusV2AJX2rLe3adummV28fqc4JSRYmWbhs2bKx3AVJkiRpvTQP2km2BD4JvKmqfr62RUdoq7W0P7Kx6uyqmlNVc6ZNm7b+nZUkSZLGSNOgnWQKvZD9kar6VNd8dzcchO75nq59KTCjb/XpwJ1d+/QR2iVJkqRxq+VVRwL8B3BTVZ3RN+siYNWdRo4FLuxrPzrJpkl2p3fS41Xd8JL7khzQbfOYvnUkSZKkcanlnSGfDbwauD7JdV3b3wHvBC5IcjywGDgKoKpuSHIBcCO9K5a8vqoe7NY7ETgH2Ay4uHtIkiRJ41azoF1VX2Pk8dUAh65hndOB00doXwjsM3a9kyRJktryzpCSJElSAwZtSZIkqQGDtiRJktSAQVuSJElqwKAtSZIkNWDQliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgMGbUmSJKkBg7YkSZLUgEFbkiRJasCgrQlr0uQpJBnKY9fdZg579yVJ0jg3edgdkB6tB1eu4JIb7x9K7bl7bT6UupIkaeLwiLYkSZLUgEFbkiRJasCgLUmSJDVg0JYkSZIaMGhLkiRJDRi0JUmSpAYM2pIkSVIDBm1JkiSpAYO2JEmS1IBBW5IkSWrAoC1JkiQ1YNCWJEmSGjBoS5IkSQ0YtCVJkqQGDNqSJElSAwZtSZIkqQGDtiRJktSAQVuSJElqwKAtSZIkNdAsaCf5YJJ7kny3r227JJcmubV73rZv3ilJbktyS5IX97Xvl+T6bt57k6RVnyVJkqSx0vKI9jnA3NXa3gJcVlV7AJd1r0myF3A0sHe3zvuTTOrWOQs4Adije6y+TUmSJGncaRa0q+orwI9Xaz4cmN9NzweO6GtfUFUPVNXtwG3A/kl2BrauqiuqqoBz+9aRJEmSxq1Bj9HeqaruAuied+zadwGW9C23tGvbpZtevV2SJEka18bLyZAjjbuutbSPvJHkhCQLkyxctmzZmHVOkiRJWl+DDtp3d8NB6J7v6dqXAjP6lpsO3Nm1Tx+hfURVdXZVzamqOdOmTRvTjkuSJEnrY9BB+yLg2G76WODCvvajk2yaZHd6Jz1e1Q0vuS/JAd3VRo7pW0eSJEkatya32nCS84FDgB2SLAVOBd4JXJDkeGAxcBRAVd2Q5ALgRmAl8PqqerDb1In0rmCyGXBx95AkSZLGtWZBu6rmrWHWoWtY/nTg9BHaFwL7jGHXJEmSpOaaBW2ptclTpjB3r82HUnuTTacOpa4kSZo4DNqasFauWEF9Y/66F2wgBx677oUkSdJGbbxc3k+SJEnaoBi0JUmSpAYM2pIkSVIDBm1JkiSpAYO29ChMmjyFJAN/7LrbzGHvuiRJGiWvOiI9Cg+uXMElN94/8LrDupyhJElafx7RliRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgMGbUmSJKkBg7YkSZLUgEFbkiRJasCgLU0gw7pRjjfLkSRp/XnDGmkCGdaNcsCb5UiStL48oi1JkiQ1YNCWJEmSGjBoS5IkSQ0YtCVJkqQGPBlSehQmT5niyYGSJGmtDNrSo7ByxQrqG/MHXjcHHjvwmpIk6dFx6IgkSZLUgEFbkiRJasChI9IEMsyx4ZOnbEKSgdedsetuLL5j0cDrSpL0WBm0pQlkWGPDoTc+fBh3pfSkU0nSROXQEUmSJKkBg7akcW3S5CkkGcpj191mDnv3JUkTmENHJI1rD65cMZQhK+CwFUnSY+MRbUlag2EdTR/mkfRdd5s5lH3edOpmG917LWnD5xFtSaOyMd4Nc1hH04f5Pi9ZfMfQ9nlje68lbfgM2pJGZVhXPJny3NcahjYCkyYP54vcJptOHXhNSRsPg7akcW2YlzQcVsgf1jXLh+nBlcP5d86Bxw68pqSNx4QJ2knmAu8BJgEfqKp3DrlLkjZwwzyKPyyTp2wylC8XkyZPGXhNSWptQgTtJJOA/wu8EFgKfCvJRVV143B7Jkljb9g3JtqYjiyvOuF1GIZ119Ndd5vJksV3DLwueKdXbXwmRNAG9gduq6ofACRZABwOGLQlSY/aMEfoLF26ZCghf/IQ/3owrH1+/NZb8dOf/XzgdQG2efzW/Ozn9w287jD3Wb+Vqhp2H9YpySuAuVX12u71q4FnVtVJqy13AnBC9/KpwC0D7WjPDsC9Q6g7zNobW91h1nafN47a7vOGX3eYtd3njaP2xlZ3mLV3q6ppI82YKEe0R/r6+4hvCFV1NnB2++6sWZKFVTVnY6q9sdUdZm33eeOo7T5v+HWHWdt93jhqb2x1h117TSbKDWuWAjP6Xk8H7hxSXyRJkqR1mihB+1vAHkl2T7IJcDRw0ZD7JEmSJK3RhBg6UlUrk5wEfIHe5f0+WFU3DLlbazLMoSvDqr2x1R1mbfd546jtPm/4dYdZ233eOGpvbHWHXXtEE+JkSEmSJGmimShDRyRJkqQJxaAtSZIkNWDQHkNJ5ia5JcltSd4ywLofTHJPku8OqmZXd0aS/05yU5IbkrxxQHWnJrkqybe7uqcNom5f/UlJrk3yuQHXXZTk+iTXJVk4wLrbJPlEkpu7f+tnDajuU7t9XfX4eZI3Daj2X3Y/W99Ncn6SqYOo29V+Y1f3hpb7O9LnRpLtklya5NbuedsB1j6q2+eHkjS5PNca6v5r97P9nSSfTrLNAGv/Y1f3uiRfTPLEQdTtm/fXSSrJDoOom+RtSX7Y93/6JWNdd021u/a/6H5H35DkXwZRN8nH+vZ3UZLrxrruWmrPSvLNVb8zkuw/oLpPT3JF9/vqs0m2blB3xPwxqM+w9VJVPsbgQe8kze8DTwI2Ab4N7DWg2gcDs4HvDnifdwZmd9NbAd8bxD7Tu676lt30FOBK4IAB7vfJwEeBzw34/V4E7DDIml3d+cBru+lNgG2G0IdJwI/o3RSgda1dgNuBzbrXFwDHDWg/9wG+C2xO72T1LwF7NKr1iM8N4F+At3TTbwH+eYC196R3o7HLgTkDrPsiYHI3/c8D3uet+6bfAPzbIOp27TPoXWDgjhafK2vY37cBf93i/R1F7ed1/5827V7vOKj3um/+u4G/H+A+fxH4/W76JcDlA6r7LeC53fRrgH9sUHfE/DGoz7D1eXhEe+w8fJv4qvoNsOo28c1V1VeAHw+i1mp176qqa7rp+4Cb6IWU1nWrqn7RvZzSPQZyVm+S6cBLgQ8Mot6wdUciDgb+A6CqflNVPx1CVw4Fvl9Vdwyo3mRgsyST6YXeQV23f0/gm1V1f1WtBL4MvKxFoTV8bhxO74sV3fMRg6pdVTdVVdO7+a6h7he79xrgm/Tu0zCo2v33x96CBp9ja/n98P8Cf9Oi5jrqNreG2icC76yqB7pl7hlQXQCSBPhD4PyxrruW2gWsOpr8eBp8jq2h7lOBr3TTlwIvb1B3TfljIJ9h68OgPXZ2AZb0vV7KAELneJFkJrAvvaPLg6g3qfsT3D3ApVU1kLrAmfR+OT00oHr9CvhikquTnDCgmk8ClgEf6obLfCDJFgOq3e9oGv2CWl1V/RB4F7AYuAv4WVV9cRC16R3NPjjJ9kk2p3cUasY61hlLO1XVXdD7RQbsOMDa48FrgIsHWTDJ6UmWAK8E/n5ANQ8DflhV3x5EvdWc1A2X+eCA/6z/FOA5Sa5M8uUkzxhgbYDnAHdX1a0DrPkm4F+7n693AacMqO53gcO66aNo/Bm2Wv4Yd59hBu2xM6rbxG+IkmwJfBJ402pHaJqpqgeraha9o0/7J9mndc0kfwDcU1VXt661Bs+uqtnA7wOvT3LwAGpOpvdnwbOqal/gl/T+HDcw6d2k6jDg4wOqty29oyK7A08EtkjyqkHUrqqb6A1fuBS4hN4QtJVrXUljIslb6b3XHxlk3ap6a1XN6Oqe1Lpe9wXurQwo1K/mLODJwCx6X2LfPcDak4FtgQOANwMXdEeZB2UeAzpY0OdE4C+7n6+/pPvL5AC8ht7vqKvpDev4TatCw8gf68ugPXY2ytvEJ5lC74f8I1X1qUHX74YxXA7MHUC5ZwOHJVlEb2jQ85N8eAB1AaiqO7vne4BP0xuu1NpSYGnfXww+QS94D9LvA9dU1d0DqvcC4PaqWlZVK4BPAQcOqDZV9R9VNbuqDqb3J9lBHgG7O8nOAN3zmP95fTxKcizwB8ArqxvcOQQfpcGf2EfwZHpfIr/dfZZNB65J8oTWhavq7u4gyUPAvzOYz7BVlgKf6oYeXkXvr5JjfhLoSLohaEcCHxtEvT7H0vv8gt6BioG831V1c1W9qKr2o/fl4vst6qwhf4y7zzCD9tjZ6G4T3x0N+A/gpqo6Y4B1p626MkCSzegFo5tb162qU6pqelXNpPfv+19VNZAjnUm2SLLVqml6J3A1v8pMVf0IWJLkqV3TocCNreuuZtBHghYDByTZvPsZP5Te+L+BSLJj97wrvV/Og9z3i+j9cqZ7vnCAtYciyVzgb4HDqur+Adfeo+/lYQzmc+z6qtqxqmZ2n2VL6Z1U9qPWtVcFoM7LGMBnWJ/PAM/v+vEUeid23zug2i8Abq6qpQOqt8qdwHO76eczoC/tfZ9hjwP+N/BvDWqsKX+Mv8+wYZ+NuSE96I2n/B69b29vHWDd8+n9GW4FvQ/N4wdU9yB6w2O+A1zXPV4ygLq/B1zb1f0ujc7iXkcfDmGAVx2hN1b6293jhgH/fM0CFnbv92eAbQdYe3NgOfD4Af/7nkYv9HwXOI/uSgUDqv1Vel9mvg0c2rDOIz43gO2By+j9Qr4M2G6AtV/WTT8A3A18YUB1b6N3fs2qz7Axv/LHWmp/svsZ+w7wWWCXQdRdbf4i2lx1ZKT9PQ+4vtvfi4CdB/hebwJ8uHu/rwGeP6j3GjgH+PMW+7qOfT4IuLr7LLkS2G9Add9ILwt9D3gn3V3Ix7juiPljUJ9h6/PwFuySJElSAw4dkSRJkhowaEuSJEkNGLQlSZKkBgzakiRJUgMGbUmSJKkBg7YkSZLUgEFbksaxJNskeV03/cQknxh2nx6LJEck2WvY/ZCkQTBoS9L4tg3wOoCqurOqXjHk/jxWRwAGbUkbBYO2JI1v7wSenOS6JB9P8l2AJMcluTDJJUluSXLq2jaS5DNJrk5yQ5IT+tp/keSfu3lfSrJ/ksuT/CDJYd0yU5N8KMn1Sa5N8ry+Pryvb1ufS3JI33ZPT/LtJN9MslOSA+ndavxfu/158li/WZI0nhi0JWl8ewvw/aqaBbx5tXn7A68EZgFHJZmzlu28pqr2A+YAb0iyfde+BXB5N+8+4O3AC+ndEv0fumVeD1BVTwPmAfOTTF1Hv7cAvllVTwe+AvxpVX2D3q2331xVs6rq++vYhiRNaAZtSZq4Lq2q5VX1K+BTwEFrWfYNSb4NfBOYAezRtf8GuKSbvh74clWt6KZndu0HAecBVNXNwB3AU9bRt98An+umr+7bliRtNCYPuwOSpEet1vEagG44xwuAZ1XV/UkuB1YdkV5RVavWewh4AKCqHkqy6ndE1lB/Jb97wKb/KHf/dh/E3zeSNkIe0Zak8e0+YKs1zHthku2SbEbvJMOvr2G5xwM/6UL2/wQOWM8+fIXeEBWSPAXYFbgFWATMSvK4JDPoDWVZl7XtjyRtUAzakjSOVdVy4OvdSZD/utrsr9Eb0nEd8MmqWriGzVwCTE7yHeAf6Q0fWR/vByYluR74GHBcVT1AL9jfTm+YybuAa0axrQXAm7uTKj0ZUtIGLb/9y54kaaJIchwwp6pOGnZfJEkj84i2JEmS1IBHtCVpA9Fdsu+yEWYd2g1BkSQNkEFbkiRJasChI5IkSVIDBm1JkiSpAYO2JEmS1IBBW5IkSWrg/wea3WpylwlMHgAAAABJRU5ErkJggg==\n",
      "text/plain": [
       "<Figure size 864x504 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create histogram of tip_amount by vendor\n",
    "plt.figure(figsize=(12,7))\n",
    "ax = sns.histplot(data=df,x='tip_amount',bins=range(0,21,1),\n",
    "                 hue='VendorID',\n",
    "                 multiple='stack',\n",
    "                 palette='pastel')\n",
    "ax.set_xticks(range(0,21,1))\n",
    "ax.set_xticklabels(range(0,21,1))\n",
    "plt.title('Tip amount by vendor histogram')\n",
    "#==> ENTER YOUR CODE HERE"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Next, zoom in on the upper end of the range of tips to check whether vendor one gets noticeably more of the most generous tips."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Text(0.5, 1.0, 'Tip amount by vendor histogram')"
      ]
     },
     "execution_count": 17,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 864x504 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create histogram of tip_amount by vendor for tips > $10 \n",
    "plt.figure(figsize=(12,7))\n",
    "ax = sns.histplot(data=df[df['tip_amount'] > 10],x='tip_amount',bins=range(10,21,1),\n",
    "                 hue='VendorID',\n",
    "                 multiple='stack',\n",
    "                 palette='pastel')\n",
    "ax.set_xticks(range(10,21,1))\n",
    "ax.set_xticklabels(range(10,21,1))\n",
    "plt.title('Tip amount by vendor histogram')\n",
    "#==> ENTER YOUR CODE HERE"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Mean tips by passenger count**\n",
    "\n",
    "Examine the unique values in the `passenger_count` column."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "1    16117\n",
       "2     3305\n",
       "5     1143\n",
       "3      953\n",
       "6      693\n",
       "4      455\n",
       "0       33\n",
       "Name: passenger_count, dtype: int64"
      ]
     },
     "execution_count": 18,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#==> ENTER YOUR CODE HERE\n",
    "df['passenger_count'].value_counts()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>tip_amount</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>passenger_count</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>2.135758</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>1.848920</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>1.856378</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>1.716768</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>1.530264</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>1.873185</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>1.720260</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                 tip_amount\n",
       "passenger_count            \n",
       "0                  2.135758\n",
       "1                  1.848920\n",
       "2                  1.856378\n",
       "3                  1.716768\n",
       "4                  1.530264\n",
       "5                  1.873185\n",
       "6                  1.720260"
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Calculate mean tips by passenger_count\n",
    "#==> ENTER YOUR CODE HERE\n",
    "mean_tips_by_passenger_count = df.groupby(['passenger_count']).mean()[['tip_amount']]\n",
    "mean_tips_by_passenger_count"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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il133ZW//e1vvdZwyimncNhhh7H77rszcuRILr/8cr70pS+x2WabMX78eBYsWADAfffdx9ixY/ngBz/Ihz/8YZ599lkAfv7zn7PNNtuwxRZbcMABB/DKK68AxVn4E044ge233573ve99fZ6Rb5QBW5IkqV2MG9f1dsYZRd8rr3TfP2lS0T97dte+PkyZMoXLLruMBx54gMsvv5wpU6Z0GTN//nwOP/xwLrnkEqZOncrChQs588wz3+xfddVVueeeezjuuOM46aSTANhxxx25++67eeCBBzjooIP43ve+12ctf/7zn7n22mu58sorOeSQQ9h5552ZOnUqK664Itdeey0LFizg+OOP59JLL+W+++7jiCOO4Ktf/SoA+++/P/feey8PPfQQG220Eeecc86b63322We54447uOaaazj55JP7rKMRXqZPkiRJ3brjjjvYd999WXHFFQHYe++9u4x54oknWHfddVl//fUBOOywwzj99NPfDNMHH3zwm/ef//zngeLyg5/4xCd49tlnef311xu6BN4ee+zB4MGD2WyzzXjjjTcYP348AJttthkzZszgiSeeYNq0aey2224AvPHGG6y55poATJs2ja997Wu8+OKLzJs3jw9/+MNvrne//fZjueWWY+ONN+7zTHqjDNiSJEntYvLknvtWWqn3/qFDe+/vRmYu8Zjaq3B0Pj7++OP553/+Z/bZZx8mT57MKaec0ud23va2twGw3HLLMXjw4DfXtdxyy7Fw4UIyk0022YS77rqry7KHH344v/vd79hiiy2YNGkSk2v2Q+d6G3ktjXKKiCRJkrq14447cvXVVzN//nzmzZvHtdde22XMhhtuyIwZM96cX/3rX/+asWPHvtl/ySWXvHk/ZswYAF566SXWWmstAM4777xKat1ggw2YNWvWmwF7wYIFPPLIIwDMnTuXNddckwULFnDBBRdUsr3eeAZbkiRJ3dpmm23YZ5992GKLLVhnnXUYNWoUq6222iJjhgwZwi9/+UsOPPBAFi5cyDbbbMPRRx/9Zv9rr73Gtttuyz/+8Q8uuugioPjQ4oEHHshaa63Fdtttx1/+8pclrnWFFVbg0ksv5YQTTuCll15i4cKFnHTSSWyyySaceuqpbLvttqyzzjpsttlmzJ07d4m315uo6lT4QDBq1KjsbvK9JElSO3rsscfYaKONWlrDvHnz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\n",
      "text/plain": [
       "<Figure size 864x504 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create bar plot for mean tips by passenger count\n",
    "#==> ENTER YOUR CODE HERE\n",
    "data=mean_tips_by_passenger_count.tail(-1)\n",
    "pal = sns.color_palette('Greens_d',len(data))\n",
    "rank = data['tip_amount'].argsort().argsort()\n",
    "plt.figure(figsize=(12,7))\n",
    "ax = sns.barplot(x=data.index,\n",
    "                y=data['tip_amount'],\n",
    "                palette=np.array(pal[::-1])[rank])\n",
    "ax.axhline(data['tip_amount'].mean(),ls='--',color='red',label='global mean')\n",
    "ax.legend()\n",
    "\n",
    "plt.title('Mean tip amount by passenger count', fontsize=16);"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Create month and day columns**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Create a month column\n",
    "#==> ENTER YOUR CODE HERE\n",
    "df['month'] = df['tpep_pickup_datetime'].dt.month_name()\n",
    "# Create a day column\n",
    "#==> ENTER YOUR CODE HERE\n",
    "df['day'] = df['tpep_pickup_datetime'].dt.day_name()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Plot total ride count by month**\n",
    "\n",
    "Begin by calculating total ride count by month."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "March        2049\n",
       "October      2027\n",
       "April        2019\n",
       "May          2013\n",
       "January      1997\n",
       "June         1964\n",
       "December     1863\n",
       "November     1843\n",
       "February     1769\n",
       "September    1734\n",
       "August       1724\n",
       "July         1697\n",
       "Name: month, dtype: int64"
      ]
     },
     "execution_count": 22,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Get total number of rides for each month\n",
    "#==> ENTER YOUR CODE HERE\n",
    "monthly_rides = df['month'].value_counts()\n",
    "monthly_rides"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Reorder the results to put the months in calendar order."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 23,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "January      1997\n",
       "February     1769\n",
       "March        2049\n",
       "April        2019\n",
       "May          2013\n",
       "June         1964\n",
       "July         1697\n",
       "August       1724\n",
       "September    1734\n",
       "October      2027\n",
       "November     1843\n",
       "December     1863\n",
       "Name: month, dtype: int64"
      ]
     },
     "execution_count": 23,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Reorder the monthly ride list so months go in order\n",
    "#==> ENTER YOUR CODE HERE\n",
    "month_order = ['January', 'February', 'March', 'April', 'May', 'June', 'July',\n",
    "         'August', 'September', 'October', 'November', 'December']\n",
    "\n",
    "monthly_rides = monthly_rides.reindex(index=month_order)\n",
    "monthly_rides"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Index(['January', 'February', 'March', 'April', 'May', 'June', 'July',\n",
       "       'August', 'September', 'October', 'November', 'December'],\n",
       "      dtype='object')"
      ]
     },
     "execution_count": 24,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Show the index\n",
    "#==> ENTER YOUR CODE HERE\n",
    "monthly_rides.index"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 864x504 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create a bar plot of total rides per month\n",
    "#==> ENTER YOUR CODE HERE\n",
    "plt.figure(figsize=(12,7))\n",
    "ax = sns.barplot(x=monthly_rides.index,y=monthly_rides)\n",
    "ax.set_xticklabels(month_order)\n",
    "plt.title('Ride count by month', fontsize=16);"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Plot total ride count by day**\n",
    "\n",
    "Repeat the above process, but now calculate the total rides by day of the week."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Monday       2931\n",
       "Tuesday      3198\n",
       "Wednesday    3390\n",
       "Thursday     3402\n",
       "Friday       3413\n",
       "Saturday     3367\n",
       "Sunday       2998\n",
       "Name: day, dtype: int64"
      ]
     },
     "execution_count": 26,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Repeat the above process, this time for rides by day\n",
    "#==> ENTER YOUR CODE HERE\n",
    "daily_rides = df['day'].value_counts()\n",
    "day_order = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday']\n",
    "\n",
    "daily_rides = daily_rides.reindex(index=day_order)\n",
    "daily_rides"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAtoAAAGtCAYAAAAoIdPXAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4yLjEsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+j8jraAAAgAElEQVR4nO3debglVX3v//dHQMUBRWmRdKPwUxwAvUQ6BENUot5IjAZN9AYnwCFNvJjojXqvaIyQhEyOUQMREQHHtDFcOooDooAiiA1BmkG0I620dKRxBAcU/P7+qHUu28Puw2k8q/c5p9+v56ln1161qmqd2tNnr7OqdqoKSZIkSXPrTpNugCRJkrQYGbQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLWmrkuTwJDUy/TTJfyb5myR33UTd3W5nm7u1eod3bPq80I7JC2ZZ98B2XJ7Yu11j9n1yknVber+SNGrbSTdAkibkmcB64J7A04Gj2vyfjNT5KPBoYMMWb938dTjDZ8dJE26HJM17Bm1JW6tLqmptmz8zyR7AC5O8tKp+DlBVG4GNE2uhJGlBc+iIJA0uBrYHdpoqGDd0JMndkhyX5NtJbkyyClg2boNJHpfkrCQ3JPlhkk8k2Xs2jWnrnpnk+23dLyV54cjy7ZL8dZJ1bfjLunZ/u5E6U0M3Dpy27XF/17ok701ySJIr2z5XJ/nNkTpnA48DDhgZenP2LP6ce7WhHN9N8oMk70ty35Htrkly2phjMNX+J93OsXpCkouT/KQNAzpiE/WOafW+n+T6JJ9Osv/I8vu3Y/nSMeseneRHSXacxd8rSYBBW5Km7AZ8H/j27dR7B/Ai4E3A7wNXAe+fXinJ7wJnATcCzwWezTA05bNJdp1pB0kObuveGTgCOJhhqMYDR6qdArwKOBV4CvBu4P+08jvqMcDLgdcCfwhsA3wkyb3b8v8J/AdwKcOQmke3stvzFqCAZwGvAX4P+NeR5ccDT0nyK9PWOwK4Gvjkpjac5OHAGcCPgUOAVwMvA54wpvpS4M3A0xiGwFwHnJvkkQBV9V/A/237Hd3HNsALgZVV9d3b/WslaUpVOTk5OW01E0PAKuChDMPndgReANwMvGQTdXdr9x8K3AK8alq941u9w0fK1gJnTau3A3A98JYZ2hdgHbAauNMm6uzd9nf0tPI/b+WPbPcPbPcPnOnvamXrgO8CO46ULW/1nj1SdjbwuVke66n9f3xa+XNa+RPa/XsCPwBeO1JnJ+Cm6cd6zD7e147p3UfKdgV+CqybYb1t2uN/FfCPY9r8mJGy32tl+0/6+evk5LSwJnu0JW2tvgz8DPgO8C7gHVX19ttZ59cZ/hO4clr5B0fvtPHeDwLel2TbqQn4EXA+8NgZ9vFQhp7rE6uNFR9jav33Tiufuv+4Gf+KTTu/frHHdk27fcAd3N6U6cfrQ8DPGXrEqaobGNr+oiRTn0vPZ/jS8e7b2fajgTOq6odTBVV1DXDe9IpJnpjkM0m+zfDF6mfAQxiO+dS6ZwNX8Iu92kcAl1bVBbfTFkn6BQZtSVurpwO/BjwZ+BTwP5Mcejvr7NJuvzWtfPr9+7XbdzGEudHpKcB92bSpZetnqHOfdjv9aij/NW355vrO6J2quqnN3nVM3c3xC8enqn7K0Hu+dKT4OIZA/+QkAVYAp1XV9GM73S7Ttz9un0kexTDE5EaGYSD7Mzz+X+K2f9/xwDOS3DfJA4GDgH++nXZI0m141RFJW6vLql11JMmnGcYdvz7Jh0d7R6eZCrY7A18bKd95Wr2pcd5HMYT46X46Q7uub7dLZ6gzFYjvD/znSPn9p+3/J+32ztPWnyno9/ALxyfJnRmG7HxzqqyqLkvyWYbe458AD2baWOlN2DB9++P2CfwBQy/271fVz0basiPwvWl1TwX+lmGIzY4M47/fN4u2SNIvsEdb0lav9dy+kqEneqaT+77AMOThf0wrP2Ta/asYxjzvVVWrx0yXzrCPr7R1X9R6dsc5ZxP7fU67Pbfdfr3dTr/SyZNn2P/tuYnh6iybY/rxeibD58/508qPA34HOBr4SlV9ehbbPp+hF/zuUwXtZNMDptW7G8P4+hqp93jGDIupqh8wBOsjGMbvv7+VSdJmsUdbkoCqWpXki8Arkry9qn48ps5VSd4P/GUbS/xF4L8zLbhWVSU5Eji99d6uZOip3hn4DeAbVfWmTbSjkrwM+Dfg00n+meFa3g8H7ldVr6uqy5N8ADi6jf3+PMNY5dcCH5gK8lW1Ick5wFFJrme4ysZzGcaP31FXMAyz+UOG3vQbquqq21lnryTvZhjL/hDgWOCcqjprWr0PM1yh5ACGq5/Mxl8zBPdPJnk9Q+/9Mdx2OMnHGa5GcnJry0MYjtc3Ge84bu1Rd9iIpDvEHm1JutWfM/Rq//EMdY5gGHv9CuA04GEMl+77BVV1BsNJi3cHTgQ+AfwDw/CO6T2509c9nSHA0/a1imHM8rqRaocBf8/Q43oGw7jjv2/lo54LXAC8FTgZ+AZDOL2j/p7h0oMnMnzReMcs1nkpw4mN/wL8DfAR4BnTK7UhHacz9JrP6jKFVXUlwxedu7Xt/x1DWD9rWr1PAH/KEOI/wnDcDmW4Osy47V7K8N+F1VV18WzaIknTpapuv5YkSZ213vm1wGer6nkTbstDGK5M80dV9a5JtkXSwuXQEUnSRCXZgWEc+bMZroH9xgm2ZRnDiZjHMJxoeZsfI5Kk2XLoiCRp0h7FcN3rZwIvrapLJtiWFwGfZhhP/+xxY/UlabYcOiJJkiR1YI+2JEmS1MGiHaO900471W677TbpZkiSJGkRu+iii66vqiXjli3aoL3bbruxevXqSTdDkiRJi1iSr29qmUNHJEmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1EG3oJ3krkkuTPKlJJcnOaaVH53km0kuadOTR9Y5KsnaJFcledJI+b5J1rRlb02SXu2WJEmS5kLPq47cBDy+qm5Msh3wuSQfa8veXFVvGK2cZE/gEGAv4FeATyV5SFXdAhwPrAAuAM4ADgI+hiRJkjRPdevRrsGN7e52bZrpZygPBj5YVTdV1dXAWmC/JLsAO1TV+TX8jOWpwNN6tVuSJEmaC13HaCfZJsklwHXAmVX1hbboJUkuTXJSkh1b2VLgmpHV17eypW1+evm4/a1IsjrJ6o0bN87p3yJJkiRtjq5Bu6puqap9gGUMvdN7MwwDeRCwD7ABeGOrPm7cdc1QPm5/J1TV8qpavmTJ2B/okSRJkraILXLVkar6HnA2cFBVfasF8J8D7wT2a9XWA7uOrLYMuLaVLxtTLkmSJM1bPa86siTJvdv89sATgS+3MddTng5c1uZXAYckuUuS3YE9gAuragNwQ5L929VGDgVO79VuSZIkaS70vOrILsApSbZhCPQrq+ojSd6TZB+G4R/rgCMAquryJCuBK4CbgSPbFUcAXgycDGzPcLURrzgiSZKkeS3DhTwWn+XLl9fq1asn3QxJkiQtYkkuqqrl45b5y5CSJElSBwZtSZIkqQODtiRJktRBz5MhJUmad97+8n+fdBMWlJe88amTboK0YNmjLUmSJHVgj7YkbWHnPPZxk27CgvO4c8+ZdBMkabMZtKWt1AFvO2DSTVhQzvuT8ybdBEnSAuPQEUmSJKkDe7QlSdIWc+xznzHpJiwor3nvv066Cfol2KMtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1sO2kG6Ct1zf+8hGTbsKC8oC/WDPpJkiSpM1gj7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktRBt6Cd5K5JLkzypSSXJzmmld8nyZlJvtpudxxZ56gka5NcleRJI+X7JlnTlr01SXq1W5IkSZoLPXu0bwIeX1X/DdgHOCjJ/sCrgLOqag/grHafJHsChwB7AQcBxyXZpm3reGAFsEebDurYbkmSJOmX1i1o1+DGdne7NhVwMHBKKz8FeFqbPxj4YFXdVFVXA2uB/ZLsAuxQVedXVQGnjqwjSZIkzUvb9tx465G+CHgw8E9V9YUkO1fVBoCq2pDkfq36UuCCkdXXt7Kftfnp5eP2t4Kh55sHPOABc/mnSJIkLWhXHvvpSTdhwXn4ax7/S63f9WTIqrqlqvYBljH0Tu89Q/Vx465rhvJx+zuhqpZX1fIlS5ZsfoMlSZKkObJFrjpSVd8DzmYYW/2tNhyEdntdq7Ye2HVktWXAta182ZhySZIkad7qedWRJUnu3ea3B54IfBlYBRzWqh0GnN7mVwGHJLlLkt0ZTnq8sA0zuSHJ/u1qI4eOrCNJkiTNSz3HaO8CnNLGad8JWFlVH0lyPrAyyQuBbwDPBKiqy5OsBK4AbgaOrKpb2rZeDJwMbA98rE2SJEnSvNUtaFfVpcCvjin/NvCETaxzLHDsmPLVwEzjuyVJkqR5xV+GlCRJkjowaEuSJEkddL2O9ny37ytPnXQTFpyLXn/opJsgSZK0INijLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkddAtaCfZNclnklyZ5PIkL23lRyf5ZpJL2vTkkXWOSrI2yVVJnjRSvm+SNW3ZW5OkV7slSZKkubBtx23fDLy8qi5Ock/goiRntmVvrqo3jFZOsidwCLAX8CvAp5I8pKpuAY4HVgAXAGcABwEf69h2SZIk6ZfSrUe7qjZU1cVt/gbgSmDpDKscDHywqm6qqquBtcB+SXYBdqiq86uqgFOBp/VqtyRJkjQXtsgY7SS7Ab8KfKEVvSTJpUlOSrJjK1sKXDOy2vpWtrTNTy8ft58VSVYnWb1x48Y5/AskSZKkzdM9aCe5B/Bh4GVV9QOGYSAPAvYBNgBvnKo6ZvWaofy2hVUnVNXyqlq+ZMmSX7rtkiRJ0h3VNWgn2Y4hZL+vqv4NoKq+VVW3VNXPgXcC+7Xq64FdR1ZfBlzbypeNKZckSZLmrZ5XHQnwLuDKqnrTSPkuI9WeDlzW5lcBhyS5S5LdgT2AC6tqA3BDkv3bNg8FTu/VbkmSJGku9LzqyAHA84A1SS5pZa8GnpVkH4bhH+uAIwCq6vIkK4ErGK5YcmS74gjAi4GTge0ZrjbiFUckSZI0r3UL2lX1OcaPrz5jhnWOBY4dU74a2HvuWidJkiT15S9DSpIkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpg25BO8muST6T5Moklyd5aSu/T5Izk3y13e44ss5RSdYmuSrJk0bK902ypi17a5L0arckSZI0F3r2aN8MvLyqHg7sDxyZZE/gVcBZVbUHcFa7T1t2CLAXcBBwXJJt2raOB1YAe7TpoI7tliRJkn5p3YJ2VW2oqovb/A3AlcBS4GDglFbtFOBpbf5g4INVdVNVXQ2sBfZLsguwQ1WdX1UFnDqyjiRJkjQvbZEx2kl2A34V+AKwc1VtgCGMA/dr1ZYC14ystr6VLW3z08vH7WdFktVJVm/cuHEu/wRJkiRps3QP2knuAXwYeFlV/WCmqmPKaoby2xZWnVBVy6tq+ZIlSza/sZIkSdIc6Rq0k2zHELLfV1X/1oq/1YaD0G6va+XrgV1HVl8GXNvKl40plyRJkuatnlcdCfAu4MqqetPIolXAYW3+MOD0kfJDktwlye4MJz1e2IaX3JBk/7bNQ0fWkSRJkualbTtu+wDgecCaJJe0slcDfwesTPJC4BvAMwGq6vIkK4ErGK5YcmRV3dLWezFwMrA98LE2SZIkSfNWt6BdVZ9j/PhqgCdsYp1jgWPHlK8G9p671kmSJEl9+cuQkiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpg1kF7STb9G6IJEmStJjMtkd7bZLXJ9mza2skSZKkRWK2QfuRwFeAE5NckGRFkh06tkuSJEla0GYVtKvqhqp6Z1X9BvC/gdcBG5KckuTBXVsoSZIkLUCzHqOd5PeSnAb8I/BG4P8D/h04o2P7JEmSpAVp21nW+yrwGeD1VfX5kfJ/TfLYuW+WJEmStLDNNmg/sqpuHLegqv50DtsjSZIkLQqzDdo3JzkS2Au461RhVb2gS6skSZKkBW62Vx15D3B/4EnAOcAy4IZejZIkSZIWutkG7QdX1WuBH1bVKcDvAo/o1yxJkiRpYZtt0P5Zu/1ekr2BewG7dWmRJEmStAjMdoz2CUl2BP4cWAXcA3htt1ZJkiRJC9yMQTvJn43cfX67/ad2e/cuLZIkSZIWgdvr0b5nu30o8GsMvdkATwXO7dUoSZIkaaGbMWhX1TEAST4JPKqqbmj3jwY+1L11kiRJ0gI125MhHwD8dOT+T/FkSEmSJGmTZnsy5HuAC5OcBhTwdOCUbq2SJEmSFrhZBe2qOjbJx4DHtKLnV9V/9GuWJEmStLDNtkebqroYuLhjWyRJkqRFY7ZjtCVJkiRtBoO2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDroF7SQnJbkuyWUjZUcn+WaSS9r05JFlRyVZm+SqJE8aKd83yZq27K1J0qvNkiRJ0lzp2aN9MnDQmPI3V9U+bToDIMmewCHAXm2d45Js0+ofD6wA9mjTuG1KkiRJ80q3oF1V5wLfmWX1g4EPVtVNVXU1sBbYL8kuwA5VdX5VFXAq8LQ+LZYkSZLmziTGaL8kyaVtaMmOrWwpcM1InfWtbGmbn14uSZIkzWtbOmgfDzwI2AfYALyxlY8bd10zlI+VZEWS1UlWb9y48ZdtqyRJknSHbdGgXVXfqqpbqurnwDuB/dqi9cCuI1WXAde28mVjyje1/ROqanlVLV+yZMncNl6SJEnaDFs0aLcx11OeDkxdkWQVcEiSuyTZneGkxwuragNwQ5L929VGDgVO35JtliRJku6IbXttOMkHgAOBnZKsB14HHJhkH4bhH+uAIwCq6vIkK4ErgJuBI6vqlrapFzNcwWR74GNtkiRJkua1bkG7qp41pvhdM9Q/Fjh2TPlqYO85bJokSZLUnb8MKUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgfdgnaSk5Jcl+SykbL7JDkzyVfb7Y4jy45KsjbJVUmeNFK+b5I1bdlbk6RXmyVJkqS50rNH+2TgoGllrwLOqqo9gLPafZLsCRwC7NXWOS7JNm2d44EVwB5tmr5NSZIkad7pFrSr6lzgO9OKDwZOafOnAE8bKf9gVd1UVVcDa4H9kuwC7FBV51dVAaeOrCNJkiTNW1t6jPbOVbUBoN3er5UvBa4Zqbe+lS1t89PLx0qyIsnqJKs3btw4pw2XJEmSNsd8ORly3LjrmqF8rKo6oaqWV9XyJUuWzFnjJEmSpM21pYP2t9pwENrtda18PbDrSL1lwLWtfNmYckmSJGle29JBexVwWJs/DDh9pPyQJHdJsjvDSY8XtuElNyTZv11t5NCRdSRJkqR5a9teG07yAeBAYKck64HXAX8HrEzyQuAbwDMBquryJCuBK4CbgSOr6pa2qRczXMFke+BjbZIkSZLmtW5Bu6qetYlFT9hE/WOBY8eUrwb2nsOmSZIkSd3Nl5MhJUmSpEXFoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHUwkaCdZl2RNkkuSrG5l90lyZpKvttsdR+oflWRtkquSPGkSbZYkSZI2xyR7tH+rqvapquXt/quAs6pqD+Csdp8kewKHAHsBBwHHJdlmEg2WJEmSZms+DR05GDilzZ8CPG2k/INVdVNVXQ2sBfabQPskSZKkWZtU0C7gk0kuSrKile1cVRsA2u39WvlS4JqRdde3sttIsiLJ6iSrN27c2KnpkiRJ0u3bdkL7PaCqrk1yP+DMJF+eoW7GlNW4ilV1AnACwPLly8fWkSRJkraEifRoV9W17fY64DSGoSDfSrILQLu9rlVfD+w6svoy4Not11pJkiRp823xoJ3k7knuOTUP/DZwGbAKOKxVOww4vc2vAg5JcpckuwN7ABdu2VZLkiRJm2cSQ0d2Bk5LMrX/91fVx5N8EViZ5IXAN4BnAlTV5UlWAlcANwNHVtUtE2i3JEmSNGtbPGhX1deA/zam/NvAEzaxzrHAsZ2bJkmSJM2Z+XR5P0mSJGnRMGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcGbUmSJKkDg7YkSZLUgUFbkiRJ6sCgLUmSJHVg0JYkSZI6MGhLkiRJHRi0JUmSpA4M2pIkSVIHBm1JkiSpA4O2JEmS1IFBW5IkSerAoC1JkiR1YNCWJEmSOjBoS5IkSR0YtCVJkqQODNqSJElSBwZtSZIkqQODtiRJktSBQVuSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDgzakiRJUgcLJmgnOSjJVUnWJnnVpNsjSZIkzWRBBO0k2wD/BPwOsCfwrCR7TrZVkiRJ0qYtiKAN7AesraqvVdVPgQ8CB0+4TZIkSdImpaom3YbbleQZwEFV9aJ2/3nAr1fVS6bVWwGsaHcfCly1RRs6t3YCrp90I7ZSHvvJ8vhPlsd/cjz2k+Xxn5yFfuwfWFVLxi3Ydku35A7KmLLbfEOoqhOAE/o3p78kq6tq+aTbsTXy2E+Wx3+yPP6T47GfLI//5CzmY79Qho6sB3Ydub8MuHZCbZEkSZJu10IJ2l8E9kiye5I7A4cAqybcJkmSJGmTFsTQkaq6OclLgE8A2wAnVdXlE25Wb4tiCMwC5bGfLI//ZHn8J8djP1ke/8lZtMd+QZwMKUmSJC00C2XoiCRJkrSgGLQlSZKkDgzacyhJJXnPyP1tk2xM8pE52v7RSV4xF9taTJLcN8klbfqvJN8cuX/nOdzPgXP1WC4USd6c5GUj9z+R5MSR+29M8mez2M5uSS7r1c62jxt7bn++mOH5/r0kV2yB/R+e5O2997OQJbll5DG6JMluY+qckeTeY8p9n5+FJK9JcnmSS9sx/vUZ6h6e5FfmYJ/rkuz0y25nsdmcx2IztrloXgcL4mTIBeSHwN5Jtq+qHwP/HfjmhNu06FXVt4F9YHhxAjdW1Rsm2qjF4/PAM4G3JLkTw48K7DCy/DeAl41bUX1s6vnewtwd/iKYZNuqunku2ih+XFX7jFuQJAznRz15C7dp0UjyaOApwKOq6qYWfmfqVDkcuIzNuCywr4fZuQOPxVbHHu259zHgd9v8s8hFmC0AAAm3SURBVIAPTC1Icp8k/7d967sgySNb+dFJTkpydpKvJfnTkXVek+SqJJ9i+LXLqfI/SvLFJF9K8uEkd0tyzyRXJ9mu1dmhfQPfbkv84fNJkpPbL4pO3b9xZP6V7dhdmuSYVnb3JB9tx/OyJH/Yyg9K8uUknwN+f2Qb+yX5fJL/aLcPbeWfTbLPSL3zph7nBeo8hjANsBfDh9UNSXZMchfg4QBJzklyUevx3qWV7duO5/nAkVMbbL1L/5bk40m+muQfRpb9dpLzk1yc5ENJ7tHK/y7JFe0xe0Mr273V/WKSvxrZxj2SnNW2sSbJwa38r5K8dKTesaOvtUVimyTvbL1Ln0yyPUB7b1ne5ndKsq7NH96O878Dn0yyS5JzW6/UZUke0+o9P8lXkpwDHDC1syRPTfKF9jr4VJKdk9ypPa5LWp07JVmbrbgnMMN/dK5MchxwMbBrRnpHfZ/fbLsA11fVTQBVdX1VXZvkL9rxuizJCRk8A1gOvK89r7efduyXJzm7zR/d1vskcGqG/x59sj2/38HIj+dl+Cy/qL3WVrSyFyZ580idP0rypi11UCZkU4/FTMd468o7VeU0RxNwI/BI4F+BuwKXAAcCH2nL3wa8rs0/HrikzR/N0HN4F4Yew28D2wH7AmuAuzH0Iq4FXtHWue/Ifv8a+JM2/27gaW1+BfDGSR+XLfwYHA28AjgZeMboY9Nuf5vhMkJh+KL5EeCxwB8A7xypf6/2GF4D7NHqrxx5LHcAtm3zTwQ+3OYPA97S5h8CrJ70MZmDY7oOeABwBPDHwF8BT2YIXOe35+6SVvcPGS6/CXAp8Lg2/3rgsjZ/OPC1kWP8dYYfpNoJOBe4e6v3f4C/AO4DXMWtV0m6d7tdBRza5o8ceYy3BXZo8zu1102A3YCLW/mdgP8cfR0txGnq+d7mdwNuBvZp91cCz23zZwPLR47JupHHYj1wn3b/5cBr2vw2wD0ZPki/ASxh6Kk6D3h7q7PjyOPyItr7DfA64GUjr7kPT/pYbeHH5RaG9/9LgNPaY/NzYP+ROuvaY+H7/OYf33u0Y/sV4LiR95n7jNR5D/DUNv//nv+jx77NLwfObvNHAxcB27f7bwX+os3/LsMvUu80ui9ge4YOiPsCd2/vK9u1ZZ8HHjHp4zWhx2KmY7xV5R17tOdYVV3K8Kb6LOCMaYt/k+HFT1V9Grhvknu1ZR+tqpuq6nrgOmBn4DHAaVX1o6r6Ab/4Iz17Z+g9XQM8h6G3EeBE4Plt/vkMT0Td6rfb9B8MPUsPYwjSa4AnJvn7JI+pqu+3ZVdX1VdreCW/d2Q79wI+lGHc8Zu59fh/CHhK+1b9AobAv9BN9Wr/BkOwPn/k/jeBvYEzk1wC/DmwrD2v711V57RtvGfaNs+qqu9X1U+AK4AHAvsDewLntW0d1sp/APwEODHJ7wM/ats4gFv/YzS6/QB/k+RS4FPAUmDnqloHfDvJr9KeAzUMw1hMrq6qS9r8RQzvRbfnzKr6Tpv/IvD8DENSHlFVNwC/zvAhubGqfgr8y8i6y4BPtPehV3Lr6+Ak4NA2/wK2vvehH1fVPm16eiv7elVdMKau7/ObqapuZAhmK4CNwL8kORz4rfYfljUMnVl7bXorm7SqhqGfMHTCvLft86PAd0fq/WmSLwEXMHQU7FFVPwQ+zfAZ8DCGwL3mDrRhwZjhsZjJVpV3HKPdxyrgDQy92fcdKc+YulMXMr9ppOwWbn1sNnWh85MZvsl9qT2pDwSoqvPavykfB2xTVV1PQJvHbqYNjUoSbh0zFuBvq+od01dIsi9DT+3ftn8drmLTx/+vgM9U1dMzjI09G6CqfpTkTOBg4H8wfJNf6D7PEKofwdBzcw1Dz+cPGD5UllbVo0dXyHCS10wX6R/3fA9D6HvW9MpJ9gOewPCrsC9h+BBlE/t4DkPv675V9bMMwyTu2padyNCLe3+GMLjYTD+u27f5//d64NZjMeWHUzNVdW6SxzL03r0nyesZHudNPZZvA95UVauSHMjQW0VVXZPkW0kezxDUn3OH/6LF44czLPN9fjNV1S0M77tntwB2BMN/lJe359/R3Pa5PmVWr4epXU1fuT3Xnwg8ur3nn80vvse8Gvgy8zT4zbUxj8VhzHyMt6q8Y492HycBfznmm+y5tA+c9kK9vn1z25Rzgae3MWX3BJ46suyewIbWczr9Q+xUhp6+reJFvgnrGL5lwxB6p8ZtfQJ4QW4d+7s0yf0ynJH+o6p6L8OXpEcxvFHunuRBbd3RAHgvbj3R9fBp+z6R4V+OXxzpKVzIzmM42eU7VXVL+5vuDTyaoXdzSYYTYkiyXZK9qup7wPeT/GbbxmyC1gXAAUke3LZ1tyQPaY/VvarqDIYTL6fGwJ/HELynb/9ewHUtZP8WQ6/4lNOAg4BfY3gubC3Wcevr4RmbqpTkgQzH7p3AuxheB18ADmzjVbdjODl2yujr4LBpmzuRoTdwZfsg1ni+z2+mJA9NssdI0T4Mw8sArm/vGaPP8xsYjuWUddz6eviDGXY1+pn9OwxDpWB43n+3heyHMfw3DoCq+gJDD/ezGTlHa7HaxGPxdWZ/jKcs2teBPdodVNV64B/HLDoaeHf7l/aPuO0H0/TtXJzkXxjGP30d+OzI4tcyfAB+nWHYw+ibyPsYxjEt+hf5DN4JnJ7kQuAsWi9FVX0yycOB84eObm4Engs8GHh9kp8DPwNeXFU/aSe5fDTJ9cDnGIZJAPwDcEqGS9t9enTHVXVRkh8wj1/4m2kNw1i6908ru0dVXZfhZKO3tuEi2wJvAS5n+FfeSUl+xCxCbVVtbL0VH8hwoiUMQ1FuYHgs78rQ6/2/2rKXAu/PcILjh0c29T7g35OsZnjtfHlkHz9N8hnge1tZ+HsDsDLJ85j2fJ3mQOCVSX7G8No4tKo2tN7B84ENDEOutmn1j2YYQvVNhi9Ku49saxXDa2CxvA668H3+DrkH8Lb2n7ObGcbzrgC+x3Cc1jEMg5pyMvDPSX7M0EFwDPCuJK9mOL6bcgzD+9HFwDkM5yoAfBz44/ZZfhXDc3/USoZzJb7L4repx+LhzO4YA4v7deBPsC9CLfgcXFXPm3Rbtkatd/xs4GFV9fMJN0cjMlyi8GLgmVX11Um3ZzHLcJWTN1fVYybdlsXI9/n5K8PvLby5qs6adFsWu4XwOrBHe5FJ8jbgdxjGGmsLS3IocCzwZ4bs+SXJngxXmTnNkN1XklcBL8ax2V34Pj8/tV7dC4EvGbL7WyivA3u0JUmSpA48GVKSJEnqwKAtSZIkdWDQliRJkjowaEuSJEkdGLQlSZKkDv5/v4Za0gDoTW4AAAAASUVORK5CYII=\n",
      "text/plain": [
       "<Figure size 864x504 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create bar plot for ride count by day\n",
    "#==> ENTER YOUR CODE HERE\n",
    "plt.figure(figsize=(12,7))\n",
    "ax = sns.barplot(x=daily_rides.index,y=daily_rides)\n",
    "ax.set_xticklabels(day_order)\n",
    "plt.title('Ride count by day', fontsize=16);"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Plot total revenue by day of the week**\n",
    "\n",
    "Repeat the above process, but now calculate the total revenue by day of the week."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>total_amount</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>day</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>Monday</th>\n",
       "      <td>49574.37</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Tuesday</th>\n",
       "      <td>52527.14</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Wednesday</th>\n",
       "      <td>55310.47</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Thursday</th>\n",
       "      <td>57181.91</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Friday</th>\n",
       "      <td>55818.74</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Saturday</th>\n",
       "      <td>51195.40</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>Sunday</th>\n",
       "      <td>48624.06</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "           total_amount\n",
       "day                    \n",
       "Monday         49574.37\n",
       "Tuesday        52527.14\n",
       "Wednesday      55310.47\n",
       "Thursday       57181.91\n",
       "Friday         55818.74\n",
       "Saturday       51195.40\n",
       "Sunday         48624.06"
      ]
     },
     "execution_count": 33,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Repeat the process, this time for total revenue by day\n",
    "#==> ENTER YOUR CODE HERE\n",
    "total_amount_day = df.groupby('day').sum()[['total_amount']]\n",
    "total_amount_day = total_amount_day.reindex(index=day_order)\n",
    "total_amount_day"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 864x504 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create bar plot of total revenue by day\n",
    "#==> ENTER YOUR CODE HERE\n",
    "plt.figure(figsize=(12,7))\n",
    "ax = sns.barplot(x=total_amount_day.index,y=total_amount_day['total_amount'])\n",
    "ax.set_xticklabels(day_order)\n",
    "ax.set_ylabel('Revenue (USD)')\n",
    "plt.title('Total revenue by day', fontsize=16);"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Plot total revenue by month**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 34,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>total_amount</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>month</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>January</th>\n",
       "      <td>31735.25</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>February</th>\n",
       "      <td>28937.89</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>March</th>\n",
       "      <td>33085.89</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>April</th>\n",
       "      <td>32012.54</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>May</th>\n",
       "      <td>33828.58</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>June</th>\n",
       "      <td>32920.52</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>July</th>\n",
       "      <td>26617.64</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>August</th>\n",
       "      <td>27759.56</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>September</th>\n",
       "      <td>28206.38</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>October</th>\n",
       "      <td>33065.83</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>November</th>\n",
       "      <td>30800.44</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>December</th>\n",
       "      <td>31261.57</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "           total_amount\n",
       "month                  \n",
       "January        31735.25\n",
       "February       28937.89\n",
       "March          33085.89\n",
       "April          32012.54\n",
       "May            33828.58\n",
       "June           32920.52\n",
       "July           26617.64\n",
       "August         27759.56\n",
       "September      28206.38\n",
       "October        33065.83\n",
       "November       30800.44\n",
       "December       31261.57"
      ]
     },
     "execution_count": 34,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Repeat the process, this time for total revenue by month\n",
    "#==> ENTER YOUR CODE HERE\n",
    "total_revenue_month = df.groupby('month').sum()[['total_amount']]\n",
    "total_revenue_month = total_revenue_month.reindex(index=month_order)\n",
    "total_revenue_month"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 37,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 864x504 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create a bar plot of total revenue by month\n",
    "#==> ENTER YOUR CODE HERE\n",
    "plt.figure(figsize=(12,7))\n",
    "ax = sns.barplot(x=total_revenue_month.index,y=total_revenue_month['total_amount'])\n",
    "ax.set_xticklabels(month_order)\n",
    "ax.set_ylabel('Revenue (USD)')\n",
    "plt.title('Total revenue by month', fontsize=16);"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "5Lx-vikocvoy"
   },
   "source": [
    "#### Scatter plot"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "You can create a scatterplot in Tableau Public, which can be easier to manipulate and present. If you'd like step by step instructions, you can review the following link. Those instructions create a scatterplot showing the relationship between total_amount and trip_distance. Consider adding the Tableau visualization to your executive summary, and adding key insights from your findings on those two variables."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "8TQjML4-0_35"
   },
   "source": [
    "[Tableau visualization guidelines](https://docs.google.com/document/d/1pcfUlttD2Y_a9A4VrKPzikZWCAfFLsBAhuKuomjcUjA/template/preview)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Plot mean trip distance by drop-off location**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 39,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "216"
      ]
     },
     "execution_count": 39,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Get number of unique drop-off location IDs\n",
    "#==> ENTER YOUR CODE HERE\n",
    "df['DOLocationID'].nunique()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 51,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>trip_distance</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>DOLocationID</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>207</th>\n",
       "      <td>1.200000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>193</th>\n",
       "      <td>1.390556</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>237</th>\n",
       "      <td>1.555494</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>234</th>\n",
       "      <td>1.727806</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>137</th>\n",
       "      <td>1.818852</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>51</th>\n",
       "      <td>17.310000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>11</th>\n",
       "      <td>17.945000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>210</th>\n",
       "      <td>20.500000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>29</th>\n",
       "      <td>21.650000</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>23</th>\n",
       "      <td>24.275000</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>216 rows × 1 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "              trip_distance\n",
       "DOLocationID               \n",
       "207                1.200000\n",
       "193                1.390556\n",
       "237                1.555494\n",
       "234                1.727806\n",
       "137                1.818852\n",
       "...                     ...\n",
       "51                17.310000\n",
       "11                17.945000\n",
       "210               20.500000\n",
       "29                21.650000\n",
       "23                24.275000\n",
       "\n",
       "[216 rows x 1 columns]"
      ]
     },
     "execution_count": 51,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Calculate the mean trip distance for each drop-off location\n",
    "#==> ENTER YOUR CODE HERE\n",
    "distance_drop_off = df.groupby('DOLocationID').mean()[['trip_distance']]\n",
    "# Sort the results in descending order by mean trip distance\n",
    "#==> ENTER YOUR CODE HERE\n",
    "distance_drop_off = distance_drop_off.sort_values(by='trip_distance')\n",
    "distance_drop_off"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 52,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 1008x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# Create a bar plot of mean trip distances by drop-off location in ascending order by distance\n",
    "#==> ENTER YOUR CODE HERE\n",
    "plt.figure(figsize=(14,6))\n",
    "ax = sns.barplot(x=distance_drop_off.index, \n",
    "                 y=distance_drop_off['trip_distance'],\n",
    "                 order=distance_drop_off.index)\n",
    "ax.set_xticklabels([])\n",
    "ax.set_xticks([])\n",
    "plt.title('Mean trip distance by drop-off location', fontsize=16);"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## BONUS CONTENT\n",
    "\n",
    "To confirm your conclusion, consider the following experiment:\n",
    "1. Create a sample of coordinates from a normal distribution&mdash;in this case 1,500 pairs of points from a normal distribution with a mean of 10 and a standard deviation of 5\n",
    "2. Calculate the distance between each pair of coordinates \n",
    "3. Group the coordinates by endpoint and calculate the mean distance between that endpoint and all other points it was paired with\n",
    "4. Plot the mean distance for each unique endpoint"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 54,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 1008x432 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#BONUS CONTENT\n",
    "\n",
    "#1. Generate random points on a 2D plane from a normal distribution\n",
    "#==> ENTER YOUR CODE HERE\n",
    "test = np.round(np.random.normal(10,5,(3000,2)),1)\n",
    "midway = int(len(test)/2)\n",
    "start = test[:midway]\n",
    "end = test[midway:]\n",
    "\n",
    "# 2. Calculate Euclidean distances between points in first half and second half of array\n",
    "#==> ENTER YOUR CODE HERE\n",
    "distance = (start-end)**2\n",
    "distance = distance.sum(axis=1)\n",
    "distance = np.sqrt(distance)\n",
    "# 3. Group the coordinates by \"drop-off location\", compute mean distance\n",
    "#==> ENTER YOUR CODE HERE\n",
    "test_df = pd.DataFrame({'start':[tuple(x) for x in start.tolist()],\n",
    "                       'end':[tuple(x) for x in end.tolist()],\n",
    "                        'distance' : distances\n",
    "                       })\n",
    "data = test_df[['end','distance']].groupby('end').mean()\n",
    "data = data.sort_values(by='distance')\n",
    "# 4. Plot the mean distance between each endpoint (\"drop-off location\") and all points it connected to\n",
    "#==> ENTER YOUR CODE HERE\n",
    "plt.figure(figsize=(14,6))\n",
    "ax = sns.barplot(x=data.index,\n",
    "                y=data['distance'],\n",
    "                order=data.index)\n",
    "\n",
    "ax.set_xticklabels([])\n",
    "ax.set_xticks([])\n",
    "ax.set_xlabel('Endpoint')\n",
    "ax.set_ylabel('Mean distance to all other points')\n",
    "ax.set_title('Mean distance between points taken randomly from normal distribution');"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Histogram of rides by drop-off location**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "First, check to whether the drop-off locations IDs are consecutively numbered. For instance, does it go 1, 2, 3, 4..., or are some numbers missing (e.g., 1, 3, 4...). If numbers aren't all consecutive, the histogram will look like some locations have very few or no rides when in reality there's no bar because there's no location. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 62,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "49"
      ]
     },
     "execution_count": 62,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# Check if all drop-off locations are consecutively numbered\n",
    "#==> ENTER YOUR CODE HERE\n",
    "df['DOLocationID'].max() - len(set(df['DOLocationID'])) \n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "To eliminate the spaces in the historgram that these missing numbers would create, sort the unique drop-off location values, then convert them to strings. This will make the histplot function display all bars directly next to each other. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 65,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 1152x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.figure(figsize=(16,4))\n",
    "#==> ENTER YOUR CODE HERE\n",
    "# DOLocationID column is numeric, so sort in ascending order\n",
    "#==> ENTER YOUR CODE HERE\n",
    "sorted_dropoffs = df['DOLocationID'].sort_values()\n",
    "# Convert to string\n",
    "#==> ENTER YOUR CODE HERE\n",
    "sorted_dropoffs = sorted_dropoffs.astype('str')\n",
    "# Plot\n",
    "sns.histplot(data=sorted_dropoffs, bins=range(0,df['DOLocationID'].max()+1,1))\n",
    "plt.xticks([])\n",
    "plt.xlabel('Drop-off locations')\n",
    "plt.title('Histogram of rides by drop-off location', fontsize=16);"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "NsvBtco1x8GN"
   },
   "source": [
    "<img src=\"images/Execute.png\" width=\"100\" height=\"100\" align=left>\n",
    "\n",
    "## PACE: Execute \n",
    "\n",
    "Consider the questions in your PACE Strategy Document to reflect on the Execute stage."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "csHAfM-RSO7l"
   },
   "source": [
    "### Task 4a. Results and evaluation\n",
    "\n",
    "Having built visualizations in Tableau and in Python, what have you learned about the dataset? What other questions have your visualizations uncovered that you should pursue? \n",
    "\n",
    "***Pro tip:*** Put yourself in your client's perspective, what would they want to know? \n",
    "\n",
    "Use the following code fields to pursue any additional EDA based on the visualizations you've already plotted. Also use the space to make sure your visualizations are clean, easily understandable, and accessible. \n",
    "\n",
    "***Ask yourself:*** Did you consider color, contrast, emphasis, and labeling?\n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "pOp0vmf1zOHO"
   },
   "source": [
    "==> ENTER YOUR RESPONSE HERE\n",
    "\n",
    "I have learned .... the highest distribution of trip distances are below 5 miles, but there are outliers all the way out to 35 miles. There are no missing values.\n",
    "\n",
    "My other questions are .... There are several trips that have a trip distance of \"0.0.\" What might those trips be? Will they impact our model?\n",
    "\n",
    "My client would likely want to know ... that the data includes dropoff and pickup times. We can use that information to derive a trip duration for each line of data. This would likely be something that will help the client with their model.\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 70,
   "metadata": {
    "id": "puYiPmvGdTJH"
   },
   "outputs": [
    {
     "ename": "TypeError",
     "evalue": "cannot subtract DatetimeArray from ndarray",
     "output_type": "error",
     "traceback": [
      "\u001b[0;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[0;31mTypeError\u001b[0m                                 Traceback (most recent call last)",
      "\u001b[0;32m<ipython-input-70-40458131b433>\u001b[0m in \u001b[0;36m<module>\u001b[0;34m\u001b[0m\n\u001b[1;32m      1\u001b[0m \u001b[0;31m#==> ENTER YOUR CODE HERE\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m----> 2\u001b[0;31m \u001b[0mdf\u001b[0m\u001b[0;34m[\u001b[0m\u001b[0;34m'trip_duration'\u001b[0m\u001b[0;34m]\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0;34m(\u001b[0m\u001b[0mdf\u001b[0m\u001b[0;34m[\u001b[0m\u001b[0;34m'tpep_dropoff_datetime'\u001b[0m\u001b[0;34m]\u001b[0m\u001b[0;34m-\u001b[0m\u001b[0mdf\u001b[0m\u001b[0;34m[\u001b[0m\u001b[0;34m'tpep_pickup_datetime'\u001b[0m\u001b[0;34m]\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m",
      "\u001b[0;32m/opt/conda/lib/python3.7/site-packages/pandas/core/ops/common.py\u001b[0m in \u001b[0;36mnew_method\u001b[0;34m(self, other)\u001b[0m\n\u001b[1;32m     67\u001b[0m         \u001b[0mother\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mitem_from_zerodim\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mother\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     68\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m---> 69\u001b[0;31m         \u001b[0;32mreturn\u001b[0m \u001b[0mmethod\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mother\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m     70\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     71\u001b[0m     \u001b[0;32mreturn\u001b[0m \u001b[0mnew_method\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/opt/conda/lib/python3.7/site-packages/pandas/core/arraylike.py\u001b[0m in \u001b[0;36m__sub__\u001b[0;34m(self, other)\u001b[0m\n\u001b[1;32m     98\u001b[0m     \u001b[0;34m@\u001b[0m\u001b[0munpack_zerodim_and_defer\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m\"__sub__\"\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     99\u001b[0m     \u001b[0;32mdef\u001b[0m \u001b[0m__sub__\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mother\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 100\u001b[0;31m         \u001b[0;32mreturn\u001b[0m \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_arith_method\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mother\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0moperator\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0msub\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    101\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    102\u001b[0m     \u001b[0;34m@\u001b[0m\u001b[0munpack_zerodim_and_defer\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m\"__rsub__\"\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/opt/conda/lib/python3.7/site-packages/pandas/core/series.py\u001b[0m in \u001b[0;36m_arith_method\u001b[0;34m(self, other, op)\u001b[0m\n\u001b[1;32m   5524\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m   5525\u001b[0m         \u001b[0;32mwith\u001b[0m \u001b[0mnp\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0merrstate\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mall\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0;34m\"ignore\"\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m-> 5526\u001b[0;31m             \u001b[0mresult\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mops\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0marithmetic_op\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mlvalues\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mrvalues\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mop\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m   5527\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m   5528\u001b[0m         \u001b[0;32mreturn\u001b[0m \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_construct_result\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mresult\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mname\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0mres_name\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/opt/conda/lib/python3.7/site-packages/pandas/core/ops/array_ops.py\u001b[0m in \u001b[0;36marithmetic_op\u001b[0;34m(left, right, op)\u001b[0m\n\u001b[1;32m    216\u001b[0m         \u001b[0;31m# Timedelta/Timestamp and other custom scalars are included in the check\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    217\u001b[0m         \u001b[0;31m# because numexpr will fail on it, see GH#31457\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 218\u001b[0;31m         \u001b[0mres_values\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mop\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mleft\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mright\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    219\u001b[0m     \u001b[0;32melse\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    220\u001b[0m         \u001b[0;31m# TODO we should handle EAs consistently and move this check before the if/else\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;32m/opt/conda/lib/python3.7/site-packages/pandas/core/arrays/datetimelike.py\u001b[0m in \u001b[0;36m__rsub__\u001b[0;34m(self, other)\u001b[0m\n\u001b[1;32m   1375\u001b[0m             \u001b[0;31m# but any other type - datetime is not well-defined.\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m   1376\u001b[0m             raise TypeError(\n\u001b[0;32m-> 1377\u001b[0;31m                 \u001b[0;34mf\"cannot subtract {type(self).__name__} from {type(other).__name__}\"\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m   1378\u001b[0m             )\n\u001b[1;32m   1379\u001b[0m         \u001b[0;32melif\u001b[0m \u001b[0mis_period_dtype\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mdtype\u001b[0m\u001b[0;34m)\u001b[0m \u001b[0;32mand\u001b[0m \u001b[0mis_timedelta64_dtype\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mother_dtype\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
      "\u001b[0;31mTypeError\u001b[0m: cannot subtract DatetimeArray from ndarray"
     ]
    }
   ],
   "source": [
    "#==> ENTER YOUR CODE HERE\n",
    "df['trip_duration'] = (df['tpep_dropoff_datetime']-df['tpep_pickup_datetime'])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 71,
   "metadata": {
    "id": "iEv7pHw-dTRP"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Unnamed: 0</th>\n",
       "      <th>VendorID</th>\n",
       "      <th>tpep_pickup_datetime</th>\n",
       "      <th>tpep_dropoff_datetime</th>\n",
       "      <th>passenger_count</th>\n",
       "      <th>trip_distance</th>\n",
       "      <th>RatecodeID</th>\n",
       "      <th>store_and_fwd_flag</th>\n",
       "      <th>PULocationID</th>\n",
       "      <th>DOLocationID</th>\n",
       "      <th>...</th>\n",
       "      <th>fare_amount</th>\n",
       "      <th>extra</th>\n",
       "      <th>mta_tax</th>\n",
       "      <th>tip_amount</th>\n",
       "      <th>tolls_amount</th>\n",
       "      <th>improvement_surcharge</th>\n",
       "      <th>total_amount</th>\n",
       "      <th>tpep_dropoff_datetimepep</th>\n",
       "      <th>month</th>\n",
       "      <th>day</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>24870114</td>\n",
       "      <td>2</td>\n",
       "      <td>2017-03-25 08:55:43</td>\n",
       "      <td>03/25/2017 9:09:47 AM</td>\n",
       "      <td>6</td>\n",
       "      <td>3.34</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>100</td>\n",
       "      <td>231</td>\n",
       "      <td>...</td>\n",
       "      <td>13.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>2.76</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>16.56</td>\n",
       "      <td>2017-03-25 09:09:47</td>\n",
       "      <td>March</td>\n",
       "      <td>Saturday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>35634249</td>\n",
       "      <td>1</td>\n",
       "      <td>2017-04-11 14:53:28</td>\n",
       "      <td>04/11/2017 3:19:58 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>1.80</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>186</td>\n",
       "      <td>43</td>\n",
       "      <td>...</td>\n",
       "      <td>16.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>4.00</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>20.80</td>\n",
       "      <td>2017-04-11 15:19:58</td>\n",
       "      <td>April</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>106203690</td>\n",
       "      <td>1</td>\n",
       "      <td>2017-12-15 07:26:56</td>\n",
       "      <td>12/15/2017 7:34:08 AM</td>\n",
       "      <td>1</td>\n",
       "      <td>1.00</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>262</td>\n",
       "      <td>236</td>\n",
       "      <td>...</td>\n",
       "      <td>6.5</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>1.45</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>8.75</td>\n",
       "      <td>2017-12-15 07:34:08</td>\n",
       "      <td>December</td>\n",
       "      <td>Friday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>38942136</td>\n",
       "      <td>2</td>\n",
       "      <td>2017-05-07 13:17:59</td>\n",
       "      <td>05/07/2017 1:48:14 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>3.70</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>188</td>\n",
       "      <td>97</td>\n",
       "      <td>...</td>\n",
       "      <td>20.5</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>6.39</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>27.69</td>\n",
       "      <td>2017-05-07 13:48:14</td>\n",
       "      <td>May</td>\n",
       "      <td>Sunday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>30841670</td>\n",
       "      <td>2</td>\n",
       "      <td>2017-04-15 23:32:20</td>\n",
       "      <td>04/15/2017 11:49:03 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>4.37</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>4</td>\n",
       "      <td>112</td>\n",
       "      <td>...</td>\n",
       "      <td>16.5</td>\n",
       "      <td>0.5</td>\n",
       "      <td>0.5</td>\n",
       "      <td>0.00</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>17.80</td>\n",
       "      <td>2017-04-15 23:49:03</td>\n",
       "      <td>April</td>\n",
       "      <td>Saturday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>23345809</td>\n",
       "      <td>2</td>\n",
       "      <td>2017-03-25 20:34:11</td>\n",
       "      <td>03/25/2017 8:42:11 PM</td>\n",
       "      <td>6</td>\n",
       "      <td>2.30</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>161</td>\n",
       "      <td>236</td>\n",
       "      <td>...</td>\n",
       "      <td>9.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>0.5</td>\n",
       "      <td>2.06</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>12.36</td>\n",
       "      <td>2017-03-25 20:42:11</td>\n",
       "      <td>March</td>\n",
       "      <td>Saturday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>37660487</td>\n",
       "      <td>2</td>\n",
       "      <td>2017-05-03 19:04:09</td>\n",
       "      <td>05/03/2017 8:03:47 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>12.83</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>79</td>\n",
       "      <td>241</td>\n",
       "      <td>...</td>\n",
       "      <td>47.5</td>\n",
       "      <td>1.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>9.86</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>59.16</td>\n",
       "      <td>2017-05-03 20:03:47</td>\n",
       "      <td>May</td>\n",
       "      <td>Wednesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>7</th>\n",
       "      <td>69059411</td>\n",
       "      <td>2</td>\n",
       "      <td>2017-08-15 17:41:06</td>\n",
       "      <td>08/15/2017 6:03:05 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>2.98</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>237</td>\n",
       "      <td>114</td>\n",
       "      <td>...</td>\n",
       "      <td>16.0</td>\n",
       "      <td>1.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>1.78</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>19.58</td>\n",
       "      <td>2017-08-15 18:03:05</td>\n",
       "      <td>August</td>\n",
       "      <td>Tuesday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>8</th>\n",
       "      <td>8433159</td>\n",
       "      <td>2</td>\n",
       "      <td>2017-02-04 16:17:07</td>\n",
       "      <td>02/04/2017 4:29:14 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>1.20</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>234</td>\n",
       "      <td>249</td>\n",
       "      <td>...</td>\n",
       "      <td>9.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>0.00</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>9.80</td>\n",
       "      <td>2017-02-04 16:29:14</td>\n",
       "      <td>February</td>\n",
       "      <td>Saturday</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>9</th>\n",
       "      <td>95294817</td>\n",
       "      <td>1</td>\n",
       "      <td>2017-11-10 15:20:29</td>\n",
       "      <td>11/10/2017 3:40:55 PM</td>\n",
       "      <td>1</td>\n",
       "      <td>1.60</td>\n",
       "      <td>1</td>\n",
       "      <td>N</td>\n",
       "      <td>239</td>\n",
       "      <td>237</td>\n",
       "      <td>...</td>\n",
       "      <td>13.0</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.5</td>\n",
       "      <td>2.75</td>\n",
       "      <td>0.0</td>\n",
       "      <td>0.3</td>\n",
       "      <td>16.55</td>\n",
       "      <td>2017-11-10 15:40:55</td>\n",
       "      <td>November</td>\n",
       "      <td>Friday</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>10 rows × 21 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "   Unnamed: 0  VendorID tpep_pickup_datetime   tpep_dropoff_datetime  \\\n",
       "0    24870114         2  2017-03-25 08:55:43   03/25/2017 9:09:47 AM   \n",
       "1    35634249         1  2017-04-11 14:53:28   04/11/2017 3:19:58 PM   \n",
       "2   106203690         1  2017-12-15 07:26:56   12/15/2017 7:34:08 AM   \n",
       "3    38942136         2  2017-05-07 13:17:59   05/07/2017 1:48:14 PM   \n",
       "4    30841670         2  2017-04-15 23:32:20  04/15/2017 11:49:03 PM   \n",
       "5    23345809         2  2017-03-25 20:34:11   03/25/2017 8:42:11 PM   \n",
       "6    37660487         2  2017-05-03 19:04:09   05/03/2017 8:03:47 PM   \n",
       "7    69059411         2  2017-08-15 17:41:06   08/15/2017 6:03:05 PM   \n",
       "8     8433159         2  2017-02-04 16:17:07   02/04/2017 4:29:14 PM   \n",
       "9    95294817         1  2017-11-10 15:20:29   11/10/2017 3:40:55 PM   \n",
       "\n",
       "   passenger_count  trip_distance  RatecodeID store_and_fwd_flag  \\\n",
       "0                6           3.34           1                  N   \n",
       "1                1           1.80           1                  N   \n",
       "2                1           1.00           1                  N   \n",
       "3                1           3.70           1                  N   \n",
       "4                1           4.37           1                  N   \n",
       "5                6           2.30           1                  N   \n",
       "6                1          12.83           1                  N   \n",
       "7                1           2.98           1                  N   \n",
       "8                1           1.20           1                  N   \n",
       "9                1           1.60           1                  N   \n",
       "\n",
       "   PULocationID  DOLocationID  ...  fare_amount  extra  mta_tax  tip_amount  \\\n",
       "0           100           231  ...         13.0    0.0      0.5        2.76   \n",
       "1           186            43  ...         16.0    0.0      0.5        4.00   \n",
       "2           262           236  ...          6.5    0.0      0.5        1.45   \n",
       "3           188            97  ...         20.5    0.0      0.5        6.39   \n",
       "4             4           112  ...         16.5    0.5      0.5        0.00   \n",
       "5           161           236  ...          9.0    0.5      0.5        2.06   \n",
       "6            79           241  ...         47.5    1.0      0.5        9.86   \n",
       "7           237           114  ...         16.0    1.0      0.5        1.78   \n",
       "8           234           249  ...          9.0    0.0      0.5        0.00   \n",
       "9           239           237  ...         13.0    0.0      0.5        2.75   \n",
       "\n",
       "   tolls_amount  improvement_surcharge  total_amount  \\\n",
       "0           0.0                    0.3         16.56   \n",
       "1           0.0                    0.3         20.80   \n",
       "2           0.0                    0.3          8.75   \n",
       "3           0.0                    0.3         27.69   \n",
       "4           0.0                    0.3         17.80   \n",
       "5           0.0                    0.3         12.36   \n",
       "6           0.0                    0.3         59.16   \n",
       "7           0.0                    0.3         19.58   \n",
       "8           0.0                    0.3          9.80   \n",
       "9           0.0                    0.3         16.55   \n",
       "\n",
       "   tpep_dropoff_datetimepep     month        day  \n",
       "0       2017-03-25 09:09:47     March   Saturday  \n",
       "1       2017-04-11 15:19:58     April    Tuesday  \n",
       "2       2017-12-15 07:34:08  December     Friday  \n",
       "3       2017-05-07 13:48:14       May     Sunday  \n",
       "4       2017-04-15 23:49:03     April   Saturday  \n",
       "5       2017-03-25 20:42:11     March   Saturday  \n",
       "6       2017-05-03 20:03:47       May  Wednesday  \n",
       "7       2017-08-15 18:03:05    August    Tuesday  \n",
       "8       2017-02-04 16:29:14  February   Saturday  \n",
       "9       2017-11-10 15:40:55  November     Friday  \n",
       "\n",
       "[10 rows x 21 columns]"
      ]
     },
     "execution_count": 71,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#==> ENTER YOUR CODE HERE\n",
    "df.head(10)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "U4HeITeOwXfo"
   },
   "source": [
    "### Task 4b. Conclusion\n",
    "*Make it professional and presentable*\n",
    "\n",
    "You have visualized the data you need to share with the director now. Remember, the goal of a data visualization is for an audience member to glean the information on the chart in mere seconds.\n",
    "\n",
    "*Questions to ask yourself for reflection:*\n",
    "Why is it important to conduct Exploratory Data Analysis? Why are the data visualizations provided in this notebook useful?\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "5o3dV6NYzNSs"
   },
   "source": [
    "\n",
    "EDA is important because ... \n",
    "==> EDA helps a data professional to get to know the data, understand its outliers, clean its missing values, and prepare it for future modeling.\n",
    "\n",
    "Visualizations helped me understand ..\n",
    "==>That this dataset has some outliers that we will need to make decisions on prior to designing a model.\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "id": "8JabFSqwwLrM"
   },
   "source": [
    "You’ve now completed professional data visualizations according to a business need. Well done! "
   ]
  }
 ],
 "metadata": {
  "colab": {
   "collapsed_sections": [],
   "provenance": []
  },
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.6"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 1
}
