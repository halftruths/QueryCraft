# QueryCraft

[Colab Notebook Demo](https://colab.research.google.com/drive/1ZZPGZSYoaNNIWeCrvDmB5CL2V4tqRcIF?usp=sharing)

## Description
QueryCraft is a self-contained Colab notebook that generates SQL queries based on a provided database schema and an English text description. It leverages the Llama3.2 language model to interpret the user's query, converting it into a corresponding SQL statement. 

The project includes an intuitive Gradio interface for input of schema details and text query intructions. Generate SQL without manually writing queries.

## Features
- **Natural Language Input**: Convert plain English questions into SQL queries.
- **Schema Interpretation**: Understands provided DB schemas to generate precise SQL statements.

## Installation & Usage
1. Open the [Colab Notebook Demo](https://colab.research.google.com/drive/1ZZPGZSYoaNNIWeCrvDmB5CL2V4tqRcIF?usp=sharing).
2. Follow the instructions in the notebook to install required dependencies.
3. Use the Gradio interface to input:
   - A database schema.
   - A query in natural language.
4. The tool will return the corresponding SQL statement based on the input.

## Example
**Input Schema:**
```sql
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255) UNIQUE
);
CREATE TABLE Classes (
    class_id INT PRIMARY KEY,
    title VARCHAR(255)
);
