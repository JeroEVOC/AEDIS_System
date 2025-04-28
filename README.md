# AEDIS System: Auburn Educational Data Intelligence System - Focus on the Automatic Report Generation Layer

## Project Description

The AEDIS System is a comprehensive application designed to automate the generation of educational performance reports and provide general trend analysis on Student Learning Outcomes (SLOs). This system integrates various data sources and technologies to streamline the assessment reporting process, offering valuable insights into academic program effectiveness.  This automatic report generation section of the project was developed using Python within the Google Drive and Jupyter Notebook environment.

## Key Features

* **Automated Report Generation:**
    * Leverages Retrieval Augmented Generation (RAG) with Gemini to create detailed reports based on a customizable and validated template.
    * Integrates data from Google Sheets (for grades and SLO data) and MongoDB (for past reports and template report).
    * Extracts contextual information from PDF documents (called "rubrics").
    * Generates reports in Word (.docx) format, saved directly to Google Drive (there is an additional test mode to save every new generated report into MongoDB).

* **Student Learning Outcome (SLO) Trend Analysis:**
    * Connects to a Milvus database to store and retrieve historical SLO data.
    * Provides "basic" interactive trend analysis, prediction, and correlation analysis of SLO scores using Gemini.
    * Users can query SLO data by degree and year.
    * Presents analysis results, including tabular data and textual interpretations as output.

* **Data Sources and Technologies:**
    * Google Sheets API:  Retrieves student grades and SLO performance data from a fixed google sheet template with a fixed structure.
    * MongoDB: A document database for the storage of report template and historical reports.
    * Milvus:  A vector database for efficient storage and retrieval of SLO data for trend analysis.
    * Google Gemini:  Generates the automatic report content and performs basic trend analysis, predictions, and correlations based on the user prompt.
    * Python:  The entire pipeline is implemented in Python.
    * PyPDF2: Extracts text from PDF documents.
    * python-docx: Creates and manipulates Word documents.
    * tabulate:  Formats data into tables for display.

## Project Structure (Conceptual)

The project is organized into the following conceptual layers:

1.  **Data Acquisition:** Fetches data from Google Sheets (grades, SLO data), MongoDB (existing sample reports + template report), and PDF files (for context learning).
2.  **Report Generation:** Generates reports using a combination of RAG+GenAI(Gemini) based on the acquired data and templates.
3.  **Trend Analysis:** Retrieves SLO data from Milvus and performs basic trend analysis using Gemini.

## Google Drive and Jupyter Notebook Implementation

This pipeline was developed using Google Drive and Jupyter Notebook.  The core components and their locations are as follows:

* **Jupyter Notebooks:** All Python code, including data retrieval, report generation, and trend analysis logic, resides in Jupyter Notebooks within Google Drive.
* **Google Sheets:** Student grades and SLO data are stored in Google Sheets. The application uses the Google Sheets API to access this data. (https://console.cloud.google.com/)
* **MongoDB:** A MongoDB Atlas database is used (https://cloud.mongodb.com/). The connection URI is within the Jupyter Notebook.
* **Milvus:** A Milvus instance is used to store SLO data for trend analysis. The connection details are within the Jupyter Notebook.
* **Report Templates:** Word document templates are stored in MongoDB.
* **Generated Reports:** Completed reports (in .docx format) are saved to a designated folder in Google Drive.
* **Service Account Credentials:** The Google Sheets API connection uses a service account, and its credentials file (JSON) is stored in Google Drive.
* **PDF Context:** The PDF files used for report context are stored in Google Drive.

**Important Notes:**

* This pipeline is designed to be run within the Google Drive/Jupyter Notebook environment.
* Ensure you have the necessary Google Cloud credentials and API keys set up (update all the corresponding sections of the entire codes with your credentials).
* You will need to configure the MongoDB and Milvus connections.
* You will find some of the Generated reports (each at different stage of finetuning process) in the GeneratedReports branch.

## Setup Instructions (General)

1.  **Google Drive:**
    * Create a folder in your Google Drive to store project files (Jupyter Notebooks, credentials, reports, etc.).
    * Upload the required Google Sheets files, PDF context files, and the service account credentials JSON file to your Google Drive.

2.  **Google Cloud:**
    * Enable the Google Sheets API in your Google Cloud project.
    * Create a service account and download the credentials JSON file.

3.  **MongoDB Atlas:**
    * Set up a MongoDB Atlas database to store report templates and historical reports.
    * Obtain the connection URI.

4.  **Milvus:**
    * Set up a Milvus instance (local or cloud-based) to store SLO data.
    * Obtain the connection details (host, port).

5.  **Jupyter Notebook:**
    * Open the Jupyter Notebook in Google Colab.
    * Update the notebook with your specific:
        * Google Sheets URLs.
        * MongoDB connection URI.
        * Milvus connection details.
        * Google API key. (https://aistudio.google.com/apikey)
        * Path to the credentials JSON file in your Google Drive.
        * Path to the PDF context file.

6.  **Dependencies:**
    * The Jupyter Notebook contains the necessary `pip install` commands for the required Python libraries (e.g., `gspread`, `pymongo`, `PyPDF2`, `google-generativeai`, `docx`, `pymilvus`, `tabulate`).

## Usage

1.  Open the main Jupyter Notebook in Google Colab.
2.  Run the notebook cells sequentially.
3.  The notebook cell of the full pipeline will prompt you for input, such as:
    * Data source (Google Sheet or local file).
    * Google Sheet URLs.
    * Report degree and year.
    * Trend analysis queries.
4.  Generated reports will be saved to your Google Drive.
5.  Trend analysis results will be displayed in the notebook.

## Action Plan

The Action Plan is incorporated into the generated report.  The system analyzes underperforming SLOs and suggests actions for improvement, which are included in the report's Action Plan section.

## Contributions

Contributions to this project are welcome!  Feel free to submit pull requests or open issues to suggest improvements or report bugs.
