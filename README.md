<h1 align="center"> Sentify </h1>
<p align="center"> Unlocking Insights from Text with Advanced Sentiment Analysis </p>

<p align="center">
  <img alt="Build" src="https://img.shields.io/badge/Build-Passing-brightgreen?style=for-the-badge">
  <img alt="Issues" src="https://img.shields.io/badge/Issues-0%20Open-blue?style=for-the-badge">
  <img alt="Contributions" src="https://img.shields.io/badge/Contributions-Welcome-orange?style=for-the-badge">
  <img alt="License" src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge">
</p>
<!-- 
  **Note:** These are static placeholder badges. Replace them with your project's actual badges.
  You can generate your own at https://shields.io
-->

## Table of Contents
- [⭐ Overview](#-overview)
- [✨ Key Features](#-key-features)
- [🛠️ Tech Stack & Architecture](#️-tech-stack--architecture)
- [🚀 Getting Started](#-getting-started)
- [🔧 Usage](#-usage)
- [🤝 Contributing](#-contributing)
- [📝 License](#-license)

## ⭐ Overview

Sentify is an open-source, AI-powered platform designed to perform efficient and accurate sentiment analysis on textual data.

> In today's data-rich environment, understanding the underlying sentiment in vast amounts of text — from customer reviews to social media feeds — is crucial for informed decision-making. Manually sifting through this data is impractical, leading to missed insights and delayed responses.

Sentify addresses this challenge by providing a robust, scalable, and easy-to-integrate solution that leverages cutting-edge machine learning models to automatically detect and classify sentiment, transforming raw text into actionable intelligence.

### Inferred Architecture
At its core, Sentify is a Python-based web service, likely built with FastAPI, providing a high-performance RESTful API for sentiment analysis. It seamlessly integrates a pre-trained suite of machine learning models and offers a user-friendly web interface for direct interaction and bulk data processing. The architecture is designed for ease of deployment, allowing developers and data scientists to quickly integrate sophisticated sentiment capabilities into their applications.

## ✨ Key Features

*   **Accurate Sentiment Prediction:** Utilizes advanced machine learning models (Random Forest, Decision Tree, XGBoost) for high-precision sentiment classification, ensuring reliable insights from your text data.
*   **Single Text Analysis:** Offers a dedicated API endpoint and web interface for instantly analyzing the sentiment of individual text inputs.
*   **Bulk Sentiment Processing:** Efficiently processes large datasets (e.g., `.csv` files) for batch sentiment analysis, generating comprehensive insights quickly.
*   **Intuitive Web Interface:** Provides a user-friendly front-end (`index.html`, `landing.html`) for effortless interaction, data upload, and direct visualization of results.
*   **Sentiment Distribution Visualization:** Generates insightful graphs depicting the overall sentiment distribution within your analyzed datasets, aiding in trend identification and deeper understanding.
*   **Scalable RESTful API:** Built on a robust framework, the API is designed for performance and easy integration into existing applications, allowing programmatic access to all sentiment analysis capabilities.
*   **Flexible Model Integration:** Leverages a collection of pre-trained models and a `CountVectorizer` for robust text feature extraction, offering a versatile approach to sentiment detection.

## 🛠️ Tech Stack & Architecture

Sentify is built using a modern and efficient technology stack, ensuring high performance, scalability, and ease of use.

| Technology      | Purpose                                    | Why it was Chosen                                                 |
| :-------------- | :----------------------------------------- | :---------------------------------------------------------------- |
| **Python**      | Core programming language                  | For its extensive data science ecosystem, readability, and versatility. |
| **FastAPI**     | Web API Framework                          | For its high performance, async support, automatic documentation (OpenAPI), and developer friendliness. |
| **Uvicorn**     | ASGI Web Server                            | The recommended ASGI server for FastAPI, ensuring fast and efficient request handling. |
| **Scikit-learn**| Machine Learning Library                   | Provides robust implementations for various ML algorithms (Random Forest, Decision Tree), data preprocessing (Scaler), and text vectorization (CountVectorizer). |
| **XGBoost**     | Gradient Boosting Library                  | A highly optimized and powerful library for implementing gradient boosting models, known for its performance and accuracy. |
| **Pandas**      | Data Manipulation & Analysis               | Essential for efficient handling, processing, and analysis of structured data, particularly CSV files for bulk operations. |
| **Matplotlib/Seaborn**| Data Visualization Library             | For generating high-quality static, interactive, and animated visualizations, crucial for sentiment distribution graphs. |
| **HTML/CSS/JS** | Frontend Web Interface                     | For creating responsive and interactive user interfaces to interact with the sentiment analysis service. |
| **`pickle`**    | Model Persistence                          | Standard Python library for serializing and deserializing Python objects, used to save and load trained ML models and preprocessors. |

## 🚀 Getting Started

Follow these steps to get Sentify up and running on your local machine.

### Prerequisites

Before you begin, ensure you have the following installed:

*   **Python:** Version 3.8 or higher
    *   [Download Python](https://www.python.org/downloads/)
*   **Git:** For cloning the repository
    *   [Download Git](https://git-scm.com/downloads)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your_username/Darsh-8-Sentify-6310c2c.git
    cd Darsh-8-Sentify-6310c2c
    ```

2.  **Create a virtual environment:**
    It's recommended to use a virtual environment to manage project dependencies.
    ```bash
    python -m venv venv
    ```

3.  **Activate the virtual environment:**
    *   **On Windows:**
        ```bash
        .\venv\Scripts\activate
        ```
    *   **On macOS/Linux:**
        ```bash
        source venv/bin/activate
        ```

4.  **Install dependencies:**
    Create a `requirements.txt` file in the root directory with the following content:
    ```
    fastapi==0.111.0
    uvicorn[standard]==0.29.0
    pandas==2.2.2
    numpy==1.26.4
    scikit-learn==1.4.2
    xgboost==2.0.3
    matplotlib==3.8.4
    python-multipart==0.0.9
    ```
    Then, install the dependencies:
    ```bash
    pip install -r requirements.txt
    ```

## 🔧 Usage

### Running the Application

Once all dependencies are installed, you can start the Sentify API and web interface:

```bash
uvicorn main:app --reload
```
This command will start the Uvicorn server, typically accessible at `http://localhost:8000`.

### Accessing the Web Interface

Open your web browser and navigate to:
[http://localhost:8000](http://localhost:8000)

Here you can interact with the application, perform single predictions, and upload CSV files for bulk analysis.

### API Usage (Example `curl` commands)

The Sentify API provides several endpoints for programmatic access:

1.  **Single Sentiment Prediction:**
    ```bash
    curl -X POST "http://localhost:8000/predict" \
         -H "Content-Type: application/json" \
         -d '{
               "text": "This product is absolutely amazing, I love it!"
             }'
    ```
    Expected output (example):
    ```json
    {
      "text": "This product is absolutely amazing, I love it!",
      "sentiment": "Positive",
      "probability": 0.95
    }
    ```

2.  **Bulk Sentiment Prediction (CSV Upload):**
    First, ensure you have a CSV file (e.g., `SentimentBulk.csv` from the `Data/` folder) with a column containing the text you want to analyze.
    ```bash
    curl -X POST "http://localhost:8000/bulk_prediction" \
         -H "accept: application/json" \
         -H "Content-Type: multipart/form-data" \
         -F "file=@./Data/SentimentBulk.csv;type=text/csv" \
         -o predictions_output.csv
    ```
    This command will upload `SentimentBulk.csv`, process it, and save the predictions to `predictions_output.csv`.

3.  **Get Sentiment Distribution Graph:**
    This endpoint would typically return an image or data for a graph based on a processed dataset.
    ```bash
    # This endpoint likely serves a visualization directly or its data.
    # An example might be:
    # curl -X GET "http://localhost:8000/get_distribution_graph?filename=Predictions.csv" \
    #      -o sentiment_distribution.png
    ```
    *Note: The exact parameters and return type might vary based on implementation.*

## 🤝 Contributing

We welcome contributions to Sentify! Whether it's reporting a bug, suggesting a new feature, or submitting code, your help is invaluable.

To contribute:

1.  **Fork** the repository on GitHub.
2.  **Clone** your forked repository.
3.  **Create a new branch** for your feature or bug fix: `git checkout -b feature/your-feature-name` or `git checkout -b bugfix/issue-description`.
4.  **Make your changes**, ensuring tests pass and code adheres to project standards.
5.  **Commit your changes** with a clear and descriptive commit message.
6.  **Push** your branch to your forked repository.
7.  **Open a Pull Request** to the `main` branch of the original Sentify repository, detailing your changes and their benefits.

Please ensure your code follows good practices and includes appropriate documentation and tests.
