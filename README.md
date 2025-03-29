# Hotel Booking Analytics API

This project provides a RESTful API using Flask to handle booking-related questions and analytics. The solution leverages Retrieval-Augmented Generation (RAG) to answer questions from predefined documents, enhancing the capabilities of a basic LLM (Language Model).

## Project Overview

This API can:
- Return analytics reports
- Answer booking-related questions using RAG for accurate responses

## 🛠 Prerequisites
Ensure you have the following installed:
- Python 3.10+
- Google Colab or Local Environment
- Ngrok for public access

## Project Setup and Installation

1. **Environment Setup**
   - Install Python 3.10 or higher.
   - Use Google Colab or set up a local environment.

2. **Clone the Repository**
   ```bash
   git clone <repo-url>
   cd hotel-booking-analytics-api
   ```

3. **Install Required Packages**
   ```bash
   pip install flask pyngrok requests
   ```

4. **Ngrok Configuration**
   - Create an account at [https://dashboard.ngrok.com](https://dashboard.ngrok.com)
   - Get your auth token and authenticate:
     ```bash
     !ngrok authtoken YOUR_AUTHTOKEN
     ```

## Running the Application
1. **Start the Flask App in Colab/Local Environment**
   ```python
   from flask import Flask, request, jsonify
   app = Flask(__name__)

   @app.route('/ask', methods=['POST'])
   def ask():
       question = request.json.get('question')
       return jsonify({'answer': f'You asked: {question}, but I don\'t have a real answer yet.'})

   app.run(host="0.0.0.0", port=8000)
   ```

2. **Expose the App Using Ngrok**
   ```python
   from pyngrok import ngrok
   public_url = ngrok.connect(8000).public_url
   print("Public API URL:", public_url)
   ```

## Testing the API
1. **Send a Test Request**
   ```python
   import requests
   url = "<ngrok-url>/ask"
   response = requests.post(url, json={"question": "What is the average price of a hotel booking?"})
   print(response.json())
   ```

Expected Response:
```json
{"answer": "You asked: What is the average price of a hotel booking?, but I don't have a real answer yet."}
```

## API Endpoints
- `POST /ask` - Accepts a JSON payload with "question" and returns a response using RAG.

##  Exploratory Data Analysis (EDA)
1. Loaded booking-related data into the environment.
2. Analyzed patterns in user queries and booking behavior.
3. Identified key metrics for analytics reports.
4. Refined the question-answering approach based on insights.

##  Future Enhancements
- Integrate a robust LLM for dynamic responses.
- Store and analyze real booking data.
- Implement caching for faster responses.
- Enhance RAG by incorporating a more powerful retriever and generator.


