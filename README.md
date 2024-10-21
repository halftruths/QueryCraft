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
   - Low memory will run fine, but enabling the following runtime-type settings will allow for faster processing:
        - High-RAM
        - Hardware Accelerator GPU
3. Select 'Runtime->Run All'
4. Use the Gradio interface to input:
   - A database schema.
   - A query in English text.
5. The tool will return the corresponding SQL statement based on the input.

## Example

**Input Txt**
```txt
"How many teachers teach only one class?"
```

**Input Schema:**
```sql
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(255),
    email VARCHAR(255) UNIQUE
);

CREATE TABLE Teachers (
    teacher_id INT PRIMARY KEY,
    name VARCHAR(255),
    specialty VARCHAR(255)
);

CREATE TABLE Classes (
    class_id INT PRIMARY KEY,
    title VARCHAR(255),
    teacher_id INT,
    FOREIGN KEY (teacher_id) REFERENCES Teachers(teacher_id)
);

CREATE TABLE ClassroomAssignments (
    assignment_id INT PRIMARY KEY,
    class_id INT,
    classroom VARCHAR(255),
    class_time TIME,
    FOREIGN KEY (class_id) REFERENCES Classes(class_id)
);

CREATE TABLE StudentClassAssociations (
    association_id INT PRIMARY KEY,
    student_id INT,
    class_id INT,
    FOREIGN KEY (student_id) REFERENCES Students(student_id),
    FOREIGN KEY (class_id) REFERENCES Classes(class_id)
);
```

**Output**
```sql
SELECT COUNT(*) 
FROM Teachers t
JOIN Classes c ON t.teacher_id = c.teacher_id
GROUP BY t.teacher_id
HAVING COUNT(c.class_id) = 1;
```
