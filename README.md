# ML-based-SQL-Injection-Detection

This project is a machine learning-based solution for detecting SQL injection attacks. SQL injection is a code injection technique that exploits vulnerabilities in web applications by inserting malicious SQL statements into application input fields. This can lead to unauthorized access, data manipulation, and even complete system compromise.

## Overview

The project consists of two main components:

1. **Machine Learning Model**: A Convolutional Neural Network (CNN) model trained on a dataset of SQL queries, both benign and malicious. The model learns to distinguish between safe and potentially harmful SQL statements.

2. **API Server**: A FastAPI server that exposes an endpoint for predicting whether a given input string is a potential SQL injection attack or not. The server loads the pre-trained CNN model and uses it to make predictions.

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/ML-based-SQL-Injection-Detection.git



Install the required dependencies:

2. Clone the repository:

   ```bash
   cd ML-based-SQL-Injection-Detection
   pip install -r requirements.txt



## Usage
1. Start the FastAPI server:
    ```bash
    uvicorn API.main:app --reload


The server will be running at http://127.0.0.1:8000.

2. Send a POST request to the /pred/ endpoint with the input string as the request body:
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"input": "SELECT * FROM users WHERE id = 1 OR 1=1;"}' http://127.0.0.1:8000/pred/

The server will respond with a JSON object indicating whether the input string is a potential SQL injection attack or not.

You can also use the sqlifree package to make predictions directly from your Python code:
```bash
    import sqlifree
    
    sql = sqlifree.prediction("[Input the SQL injection here]")

    if sql:
        print("It's SQL Injection!")
    else:
        print("Safe SQL query")