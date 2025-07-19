# Micro Habit Tracker

A simple habit tracking application built using **pure PHP** and **MySQL** for the backend. This project is designed to help users track their daily habits efficiently and intuitively. The application is intended to run locally using the **XAMPP** server stack.

## Features

- User registration and authentication
- Add, edit, and delete habits
- Mark habits as complete/incomplete for each day
- View habit progress and history
- Simple and clean UI

## Technologies Used

- **Backend:** PHP (no frameworks, pure PHP)
- **Database:** MySQL
- **Server:** XAMPP (Apache + MySQL)
- **Frontend:** HTML, CSS, (optionally JavaScript for enhanced UI)

## Installation

1. **Clone the repository:**
    ```bash
    git clone https://github.com/tanishchopra15/micro-habit_tracker.git
    ```

2. **Setup XAMPP:**
    - Download and install [XAMPP](https://www.apachefriends.org/index.html) if you haven't already.
    - Start Apache and MySQL from the XAMPP Control Panel.

3. **Import the Database:**
    - Open phpMyAdmin (`http://localhost/phpmyadmin`).
    - Create a new database (e.g., `habit_tracker`).
    - Import the provided SQL file (if available) or manually create the required tables as described below.

4. **Configure Database Connection:**
    - Update the database connection settings in your PHP files (look for `config.php` or similar):
        ```php
        $host = 'localhost';
        $db   = 'habit_tracker';
        $user = 'root';
        $pass = '';
        $charset = 'utf8mb4';
        ```

5. **Move Project Files:**
    - Copy or move the contents of this repository to your XAMPP `htdocs` directory (e.g., `C:\xampp\htdocs\micro-habit_tracker`).

6. **Access the Application:**
    - In your browser, navigate to [http://localhost/micro-habit_tracker](http://localhost/micro-habit_tracker).

## Example Database Structure

You can use the following SQL to create a basic structure:

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL
);

CREATE TABLE habits (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

CREATE TABLE habit_logs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    habit_id INT NOT NULL,
    log_date DATE NOT NULL,
    is_complete BOOLEAN DEFAULT FALSE,
    FOREIGN KEY (habit_id) REFERENCES habits(id)
);
