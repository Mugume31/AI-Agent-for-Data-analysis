# AI-Agent-for-Data-analysis
AI Agent for Data Analysis is an intelligent assistant powered by Google's Gemini Pro and LangChain, designed to analyze business data stored in Google Sheets using natural language queries

**Features**
Connects to a Google Sheet via gspread

Loads and converts Google Sheet data into a Pandas DataFrame

Uses Gemini 2.0 Flash via langchain_google_genai as the LLM

Implements a LangChain Pandas Agent for interacting with the data

Allows users to query, summarize, and filter data using natural language

Includes a custom tool to view or summarize the dataset

**How It Works**
1. Set Up Environment Variables

Create a .env file in the root directory and add your Gemini API key:

GOOGLE_API_KEY=your_google_gemini_api_key_here
2. Install Required Dependencies

Run this command:

pip install google-generativeai langchain-google-genai langchain_experimental gspread python-dotenv oauth2client pandas

3. Service Account Setup

Ensure you have a Google Cloud service account key (JSON file), and share the target Google Sheet with the service account email.

Update the script to use your credentials file and sheet ID:

creds = ServiceAccountCredentials.from_json_keyfile_name("your_credentials.json", scope)
sheet = client.open_by_key("your_google_sheet_id").sheet1

**Usage Instructions**
 Launch the notebook or Python script.

It will:

  Authenticate to Google Sheets

  Load the data into a DataFrame

  Create a LangChain Pandas Agent connected to Gemini

  The pandas_agent.run() method lets you pass prompts like:

"The dataframe has a column called `date` (datetime), a column called `type`, and a column called `amount`.
Filter the dataframe to include:
- rows where the `date` is between January 1st 2025 and March 31st 2025
- and the `type` is equal to cost.
Then calculate the **total** of the `amount` column for these rows.
Store the result in a variable called `result` and print it:
The total cost between January 1st 2025 and March 31st 2025 is {result:,} UGX"

Output will be returned by Gemini, using the LangChain agent's interpretation of your prompt.
