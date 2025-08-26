# Excel-chat-Bot
This analytical chatbot provides precise numerical calculations and insights based on your Excel data. Simply ask your questions, and it will analyze your spreadsheets to deliver accurate results, summaries, and computations efficiently, helping you make data-driven decisions with ease.
Here’s a detailed description you can use for your GitHub README to explain your Excel analytical chatbot code:

---

# Excel Analytical Chatbot

This project is an **interactive Excel Analytical Chatbot** built using **Python**, **ipywidgets**, and **Azure OpenAI**. The chatbot allows users to upload an Excel file and ask questions about the data. It can generate precise calculations, summaries, and insights by dynamically creating Python formulas for **pandas DataFrames** based on user queries.

---

## Features

1. **Excel File Upload**

   * Users can upload a `.xlsx` file.
   * The bot reads the first sheet into a pandas DataFrame.

2. **Interactive Chat Interface**

   * Built with **ipywidgets** for Jupyter Notebook/Colab.
   * Chat-like interface with user messages on the left and bot responses on the right.
   * Includes a scrollable chat box with styled message bubbles.

3. **Natural Language Understanding**

   * Users can type questions in natural language (e.g., “Sum of Revenue for Consumer Industry”).
   * Supports both approximate and partial column names.

4. **Dynamic Formula Generation with Azure OpenAI**

   * Uses Azure OpenAI’s `chat.completions` API to generate Python formulas for pandas DataFrames.
   * Generates formulas that are **ready-to-execute**, without the need for creating new columns.
   * Can handle **categorical**, **numerical**, and **date columns** intelligently.

5. **Formula Cleaning and Evaluation**

   * Extracts executable Python code from LLM responses.
   * Evaluates formulas safely using `eval` and `ast.literal_eval` in a controlled environment.
   * Supports common operations: filtering, aggregation, sums, counts, min/max, and statistics.

6. **Friendly, Human-like Responses**

   * Converts raw results into easy-to-understand messages.
   * Acknowledges user queries and presents results in a readable, concise way.

7. **Stopwords Handling**

   * Common English stopwords and custom domain-specific words are filtered during query processing for better column matching.

8. **UI Controls**

   * `Submit` button to ask a question.
   * `Clear Chat` button to reset the chat history.
   * Chat input is disabled until a valid Excel file is uploaded.

---

## How It Works

1. **Upload Excel File**:

   * The chatbot reads the file into a pandas DataFrame (`df`).

2. **User Asks Question**:

   * The user enters a question about the dataset in natural language.

3. **Query Processing**:

   * The query is cleaned (stopwords removed) and matched against unique column values.
   * Generates a mapping of potential column-value matches to guide formula creation.

4. **Formula Generation**:

   * Sends a prompt to Azure OpenAI to generate a Python formula using the DataFrame.
   * The LLM ensures that the formula only uses existing columns and avoids creating new ones.

5. **Formula Cleaning and Execution**:

   * Removes unnecessary code wrappers.
   * Evaluates the formula using pandas, numpy, datetime, and standard Python functions.

6. **Friendly Response**:

   * Converts the computed result into a human-readable message using the LLM.

7. **Display**:

   * Updates the chat interface with both the user’s query and the bot’s response.
   * Supports Markdown tables, DataFrames, and standard text formatting.

---

## Technical Details

* **Libraries Used**:

  * `pandas` and `numpy` for data manipulation.
  * `ipywidgets` for interactive UI components.
  * `markdown` for table formatting in chat.
  * `nltk` for stopwords filtering.
  * `openai` (AzureOpenAI) for LLM-based formula generation.
  * `dotenv` for environment variable management.
* **Key Functions**:

  * `get_unique_values_for_columns()`: Generates unique values for specified columns.
  * `clean_query()`: Cleans user input by removing stopwords.
  * `match_query_to_unique_values_formatted()`: Matches query tokens to column values.
  * `generate_formula_with_llm()`: Generates Python formula using Azure OpenAI.
  * `generate_cleaned_response_with_llm()`: Converts formula to a single executable expression.
  * `evaluate_formula()`: Safely evaluates formulas.
  * `create_user_response()`: Converts results into friendly text.
  * `format_message()`: Styles messages for chat display.

---

## How to Use

1. **Setup Environment Variables**
   Create a `.env` file (`user_env.env`) with:

   ```text
   AZURE_OPENAI_API_KEY=<your_key>
   AZURE_OPENAI_API_BASE=<your_endpoint>
   AZURE_OPENAI_CHAT_API_VERSION=<api_version>
   AZURE_OPENAI_CHAT_DEPLOYMENT=<deployment_name>
   ```

2. **Install Dependencies**

   ```bash
   pip install pandas numpy ipywidgets markdown nltk openai python-dotenv
   ```

3. **Run Notebook**

   * Upload your Excel file.
   * Ask questions about the data.
   * The bot will return calculations or summaries instantly.

---

## Example Use Cases

* Sum, average, min/max of numerical columns filtered by categorical values.
* Count occurrences of a category.
* Aggregate values by date ranges.
* Analyze project or client data dynamically without manual Excel formulas.

---

This code essentially acts as a **smart Excel assistant**, bridging the gap between **natural language queries** and **pandas-based data analytics**, making it ideal for business analysts, data professionals, or anyone who wants quick insights from Excel data without writing code manually.

---
