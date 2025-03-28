# Flag Quiz App

This is a simple web application built with Node.js, Express, and PostgreSQL that quizzes users on country flags. It retrieves flag data from a PostgreSQL database and presents them to the user, allowing them to guess the corresponding country.

## Features

* Displays a random country flag.
* Allows users to input the country name.
* Provides instant feedback on whether the answer is correct.
* Keeps track of the user's total score.
* Displays a "Game Over" alert when the user answers incorrectly.
* Includes a "Restart" button to start a new quiz.
* Stylized with a background image.

## Technologies Used

* **Node.js:** JavaScript runtime environment.
* **Express.js:** Web application framework for Node.js.
* **PostgreSQL:** Relational database for storing flag data.
* **pg:** Node.js PostgreSQL client.
* **EJS (Embedded JavaScript templates):** Template engine for dynamic HTML generation.
* **Body-parser:** Middleware for parsing request bodies.
* **CSS:** For styling the application.
* **HTML:** For the structure of the web pages.

## Setup Instructions

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/Hamish404/Postgres-Read/
    cd Postgres-Read
    ```

2.  **Install Dependencies:**

    ```bash
    npm install
    ```

3.  **Set Up PostgreSQL Database:**

    * Ensure you have PostgreSQL installed and running on your local machine.
    * Create a database named `world`.
    * Create a table named `flags` with the following structure:

        ```sql
        CREATE TABLE flags (
            id INT PRIMARY KEY,
            name VARCHAR(255),
            flag VARCHAR(10)
        );
        ```

    * Import the data from `flags.csv` into the `flags` table. You can use pgAdmin or the `psql` command-line tool.

4.  **Configure Database Connection:**

    * In `index.js`, update the `db` connection details with your PostgreSQL username and password:

        ```javascript
        const db = new pg.Client({
          user: 'postgres', // Replace with your username
          password: '123456', // Replace with your password (IMPORTANT: see security note below)
          host: 'localhost',
          port: 5432,
          database: 'world'
        });
        ```

    * **Security Note:** For production environments, it is highly recommended to store your database password in environment variables or a secure configuration file instead of hardcoding it in your code.

5.  **Run the Application:**

    ```bash
    node index.js
    ```

6.  **Open in Browser:**

    * Open your web browser and navigate to `http://localhost:3000`.

## Files Included

* **index.js:** The main Node.js application file.
* **flags.csv:** Contains the flag data for the quiz.
* **public/images/background.jpg:** The background image for the application.
* **public/styles/main.css:** CSS stylesheet for the application.
* **views/index.ejs:** EJS template for the main page.

## Important Security Note

* **Do not commit sensitive information like database passwords directly to your repository.** Use environment variables or secure configuration files.
* This project is for educational purposes. For production use, implement proper security measures.
