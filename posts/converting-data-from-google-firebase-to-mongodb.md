---
title: Converting Data from Google Firebase to MongoDB
date: 2023-03-24
status: publish
permalink: /converting-data-from-google-firebase-to-mongodb
description: How to convert data from Google Firebase Firestore to MongoDB using Python and pandas.
author: Tr1pwyr
type: post
id: 866
thumbnail: /uploads/images/firebase2mongo.webp
category:
    - Tech
tags:
    - google firebase
    - mongodb
    - python
    - pandas
---

# Converting Data from Google Firebase Firestore to MongoDB

Google Firebase Firestore and MongoDB are both popular NoSQL databases that offer scalability and flexibility for storing and managing data. If you're looking to migrate your data from Google Firebase Firestore to MongoDB, there are multiple approaches you can take. In this article, we'll explore one common method using JSON exports and Python's pandas library.

![Firebase to MongoDB](/uploads/images/firebase2mongo.webp)

## Exporting Data from Firebase Firestore

The first step is to export the data from Google Firebase Firestore. Firebase provides a command-line tool called "firebase-tools" that makes it easy to interact with your Firebase project from the terminal. Follow these steps to export your Firestore data:

1. Install Node.js: If you don't already have Node.js installed, download and install it from the official Node.js website (https://nodejs.org).

2. Install firebase-tools: Open a terminal and run the following command to install firebase-tools globally on your machine:

```
npm install -g firebase-tools
```

3. Authenticate with Firebase: Run the following command and follow the prompts to log in to your Firebase account:

```
firebase login
```

4. Navigate to your Firebase project directory: Use the `cd` command to navigate to the root directory of your Firebase project.

5. Export Firestore data: Run the following command to export your Firestore data to a JSON file:

```
firebase firestore:export --project <your-project-id> --output <output-file.json>
```

Replace `<your-project-id>` with the ID of your Firebase project and `<output-file.json>` with the desired file name for the exported data.

Once the export process completes, you'll have a JSON file containing your Firestore data.

## Converting Firestore Data to MongoDB Format using Python

To convert the exported Firestore data to a format suitable for MongoDB, we can leverage Python and its powerful data manipulation libraries such as pandas. Follow these steps to convert the data:

1. Install Python and pandas: If you don't have Python installed, download and install it from the official Python website (https://python.org). Then, install the pandas library by running the following command:

```
pip install pandas
```

2. Load the JSON data into a pandas DataFrame: Use the following Python code to load the exported JSON file into a pandas DataFrame:

```python
import pandas as pd

# Read the JSON file into a pandas DataFrame
data = pd.read_json('<output-file.json>')
```

Replace `<output-file.json>` with the path to the JSON file exported from Firebase.

3. Transform the data if necessary: Depending on your specific requirements and the structure of your data, you might need to perform some transformations on the DataFrame. pandas provides a wide range of functions and methods for manipulating and cleaning data. Refer to the pandas documentation (https://pandas.pydata.org/docs/) for detailed guidance on data manipulation techniques.

4. Convert the DataFrame to MongoDB documents: To convert the pandas DataFrame into a format suitable for MongoDB, we can use the `to_dict()` method with the `'records'` orientation. This will generate a list of dictionaries, where each dictionary represents a document that can be inserted into MongoDB.

```python
# Convert DataFrame to a list of dictionaries
mongo_documents = data.to_dict(orient='records')
```

5. Import the data into MongoDB: Finally, you can use the MongoDB driver for Python (such as `pymongo`) to connect to your MongoDB instance and insert the converted data. Refer to the MongoDB documentation and the documentation of the specific driver you're using for detailed instructions on connecting to MongoDB and performing data operations.
