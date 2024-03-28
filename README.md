# Natural Language to SQL Query with LangChain

## Introduction
Welcome to the repository for the Natural Language to SQL Query project powered by LangChain. This project leverages advanced Natural Language Processing (NLP) techniques to enable users to interact with databases using plain English queries, eliminating the need for complex SQL syntax.

## Features
- Translate natural language queries into SQL commands.
- Support for various SQL dialects.
- Integration with LangChain for seamless NLP processing.
- Few-shot learning for enhanced model accuracy.
- Dynamic few-shot example selection for context-aware responses.
- Dynamic relevant table selection for efficient query parsing.
- Memory integration for chatbot-like follow-up interactions.

## Articles Overview
This repository is accompanied by a series of articles authored by Pradip Nichite, providing in-depth insights into the development and implementation of the Natural Language to SQL Query system with LangChain.
[Link](https://blog.futuresmart.ai/mastering-natural-language-to-sql-with-langchain-nl2sql)

1. *Mastering Natural Language to SQL with LangChain | NL2SQL*
   - Introduction to NL2SQL and LangChain.
   - Building a Basic NL2SQL Model.
   - Incorporating Few-Shot Learning.
   - Dynamic Few-Shot Example Selection.
   - Dynamic Relevant Table Selection.
   - Enhancing Chatbots with Memory for Follow-up Database Queries.

## Installation
To get started with this project, follow these steps:
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/natural-language-to-sql.git
   cd natural-language-to-sql
   
   # Install All dependency 
   
   # RUN:

   streamlit main.py

   ```
   ```
   Local implementation Details:

   def lang2sql(table_name, query):
    # Step 1: Create the prompt
    prompt = create_message(table_name, query)
    
    # Step 2: Transform prompt into format suitable for API
    message = [
        {
          "role": "system",
          "content": prompt.system
        },
        {
          "role": "user",
          "content": prompt.user
        }
    ]
    
    # Step 3: Send prompt to OpenAI API
    response = openai.ChatCompletion.create(
        model = "gpt-3.5-turbo",
        messages = message,
        temperature = 0,
        max_tokens = 256)
    
    # Step 4: Extract SQL query from API response
    sql = response["choices"][0]["message"]["content"]
    
    # Step 5: Add quotes to variable names if necessary
    sql_with_quotes = add_quotes(sql, prompt.column_names)
    
    return sql_with_quotes
    ```
