# price-prediction-system

# BESTHomeFI

BESTHomeFI is an open-source web app that uses MindsDB AI & Node.js to predict or forecast house prices. The prediction is based on a trained machine-learning model developed using historical data on house prices. 🏡💻

BESTHomeFI is a powerful web application that can provide valuable insights to anyone interested in buying & selling property. 📈✨

## Tech Stack

- HTML, Bootstrap 3, Chart.js, EJS template engine, MindsDB JavaScript SDK (Frontend)
- Express, Node.js (Backend)
- MindsDB (Machine Learning, AI Tables)
- Linode Cloud (For Hosting MindsDB docker image, Node.js on Linode VM) 

## System Requirements

- 4 core CPU (Intel or AMD)
- 8 GB RAM
- 20 GB hard disk
- Installed latest Docker Engine
- Installed latest Node.js & NPM
- Ubuntu (Recommended) or macOS or Windows
- 4 GB data to download MindsDB Docker image

## Project Flow

1. A user who wants to predict the house price can visit the site homepage. 🌐
2. In the form, the user has to enter the values required to predict the house price. 📝
3. After submitting the form, the request is sent to the MindsDB server by the Node.js server to predict the house price for the given input. 🔄
4. The Node.js server gets the response from the MindsDB server with the data. 📊
5. The user can view the average number of rooms, median price in CA over time in the bar chart & scatter plot by clicking the dashboard page on the upper right of the homepage. 📉📈

## Installation

Steps to run the app on localhost:

1. **Clone the project from GitHub:**
    ```bash
    git clone https://github.com/bakkeshks/HomeScopeCA.git
    ```

2. **Install the dependencies:**
    ```bash
    npm install
    ```

3. **Install the latest version of MindsDB Docker Image (Docker Engine must be installed on your local machine):**
    ```bash
    docker pull mindsdb/mindsdb
    sudo systemctl start docker
    ```

4. **Download the dataset from Kaggle:**
    ```bash
    https://www.kaggle.com/datasets/
    ```

5. **Run this command to start MindsDB in Docker:**
    ```bash
    docker run -p 47334:47334 -p 47335:47335 mindsdb/mindsdb
    ```

6. **Go to `http://localhost:47334` & select the option to upload the data through files (.csv).**

7. **Import the `housing.csv` & give `home_table` as the name of the table in the datasource name field.**

8. **After you press save, it will import data to files database and it will create `home_table` in the files.**

9. **Once the table is created, you have to create & train the model with the data.**
    #### Train the Model:
    ```sql
    CREATE MODEL
    mindsdb.home_model
    FROM files
    (SELECT * FROM home_table)
    PREDICT median_house_value;
    ```

    #### Predict the Model:
    ```sql
    SELECT median_house_value
    FROM home_model
    WHERE longitude='-122.23' AND
    latitude=37.88 AND
    housing_median_age=41 AND
    total_rooms=880 AND
    total_bedrooms=129 AND
    population=322 AND
    households=126 AND
    median_income=8.3252 AND
    ocean_proximity='NEAR BAY'
    ```

10. **Now you can write the query & predict the value in the MindsDB editor.**



11. **Start the Node.js server on your machine:**
    ```bash
    node app.js 
    ```





















    
