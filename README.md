MySQL and SQLite Projects with Flask
<p align="center"> <img src="https://user-images.githubusercontent.com/54184905/109134183-d3e06480-7766-11eb-83b7-f3d44c53ebbd.png" /> </p>
Overview
This repository demonstrates how to build web applications using Flask, with integrations for both MySQL and SQLite databases. Each project showcases a different database management system, focusing on specific use cases: a blog application using MySQL and a to-do application using SQLite.

Technologies Used
Flask: A lightweight, micro web framework for Python.
MySQL: A relational database management system for the blog application.
SQLite: An embedded relational database used in the to-do app.
SQLAlchemy: ORM (Object-Relational Mapping) tool used in the SQLite project to interact with the database through Python objects.
Projects
1. demir.ai Blog with MySQL
This project is a simple blog where users can:

Register and log in.
Read and write articles.
Database Structure:

Users Table: Stores user information such as name, email, username, and password.

sql
Copy code
CREATE TABLE users (
    id INT NOT NULL AUTO_INCREMENT,
    name TEXT NOT NULL,
    email TEXT NOT NULL,
    username TEXT NOT NULL,
    password TEXT NOT NULL,
    PRIMARY KEY (id)
);
Articles Table: Stores articles with fields for title, author, content, and creation date.

sql
Copy code
CREATE TABLE articles (
    id INT NOT NULL AUTO_INCREMENT,
    title TEXT NOT NULL,
    author TEXT NOT NULL,
    content TEXT NOT NULL,
    created_date TIMESTAMP NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id)
);
Flask Configuration:

The Flask application is configured to connect to a MySQL database hosted on pythonanywhere. Here's a basic snippet of how the MySQL configuration is set up:

python
Copy code
app = Flask(__name__)
app.config["MYSQL_HOST"] = "demirai.mysql.pythonanywhere-services.com"
app.config["MYSQL_USER"] = "demirai"
app.config["MYSQL_PASSWORD"] = "****"
app.config["MYSQL_DB"] = "demirai$demirai"
app.config["MYSQL_CURSORCLASS"] = "DictCursor"
mysql = MySQL(app)
2. Todo App with SQLite
The to-do app allows users to:

Add, update, and delete tasks.
Mark tasks as complete.
ORM and SQLite Integration:

In this application, the database operations are handled via SQLAlchemy, which abstracts SQL queries into Python objects.

Tasks Table: This table stores tasks, including their titles and completion status.
python
Copy code
class Todo(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(80))
    complete = db.Column(db.Boolean)
Flask Configuration:

The application is configured to connect to a local SQLite database.

python
Copy code
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///todo.db'
db = SQLAlchemy(app)
Installation
Prerequisites
Python 3.x
MySQL (for the blog project)
SQLite (for the to-do project)
Flask and SQLAlchemy
Steps
Clone the repository:

bash
Copy code
git clone https://github.com/Charan-Cherry7/Python-Sql-1.git
Install the required dependencies:

bash
Copy code
pip install -r requirements.txt
Set up the MySQL database for the blog application by running the SQL queries in demiraiBlog/schema.sql.

For the to-do app, SQLite will automatically create the database when you run the application.

Usage
For MySQL (demir.ai blog):

Configure the database connection in the config.py or directly in the app as shown above.
Start the Flask server:
bash
Copy code
python demiraiBlog/app.py
Access the app in your browser at http://localhost:5000.
For SQLite (Todo app):

Run the following command to start the server:
bash
Copy code
python FlaskTodoApp/app.py
The to-do application will be accessible at http://localhost:5000.
Project Screenshots
<p align="center"> <img src="https://user-images.githubusercontent.com/54184905/109134181-d3e06480-7766-11eb-97e8-61ffa4ca040a.png" /> </p>
Contributing
Feel free to contribute to this project by creating issues or submitting pull requests. Contributions to add more features or improve existing ones are welcome!
