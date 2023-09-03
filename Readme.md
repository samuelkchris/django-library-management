```markdown
# Library Management System

A simple library management system built for Major Project 2021 by Abhik Bhattacharya (ID: 181001102058) & Saikat Shee (ID: 181001102053).

![HTML5](https://www.w3.org/html/logo/downloads/HTML5_Logo_64.png)
![CSS3](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/CSS3_logo_and_wordmark.svg/48px-CSS3_logo_and_wordmark.svg.png)
![Vanilla JS](https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/64px-Unofficial_JavaScript_logo_2.svg.png)
![Python](https://www.quintagroup.com/++theme++quintagroup-theme/images/logo_python_section.png)
![Django](https://www.quintagroup.com/++theme++quintagroup-theme/images/logo_django_section.png)
![Tailwind CSS](https://refactoringui.nyc3.cdn.digitaloceanspaces.com/tailwind-logo.svg)

## Features

### Anyone can:

1. View all the books on the homepage.
2. Search for books based on author, book name, or category.
3. Sort books or authors alphabetically.

### Student can:

1. Login or signup.
2. Request books.
3. View their own issues, filter them based on:
   - Requested issues
   - Issued books
   - All of them together
4. Check their fines.
5. See:
   - The days remaining to return a particular book
   - The number of days past the return date of a particular book in the "My Fines" page.
6. Pay their fines online (powered by RazorPay).

### Admin can:

1. Login to the admin dashboard.
2. Manage all issues:
   - View issues
   - Delete issues
   - Search issues by student ID
   - Filter issues based on:
     - Issued or not
     - Returned or not
3. Accept an issue:
   - Manually select return date from the dashboard
   - Automatically calculate the return date from the Issue Requests page.
4. Manage books:
   - Add, delete, search books
   - Filter books based on author
5. Manage authors:
   - Add, delete, search authors
6. Calculate fines.
7. Create, delete, search fines for student ID.
8. Toggle fine paid status (if paid in cash).
9. Search, modify, add, delete students.
10. Filter students based on department and check all fines and issues of that student.
11. See the last login, date joined, and the student associated with a particular user.
12. Change passwords for any user.

### More Features:

- Real-time validation of student IDs during signup.
- Books on the homepage show status: "issued," "issue requested," or "request issue" based on their availability.
- RazorPay integration for online fine payments.

## Project Setup

To set up and run this project on your local machine, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/library-management-system.git
   cd library-management-system
   ```

2. Create and activate a virtual environment (optional but recommended):

   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/macOS
   # or
   venv\Scripts\activate  # Windows
   ```

3. Install project dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Apply database migrations:

   ```bash
   python manage.py migrate
   ```

5. Create a superuser (admin) account:

   ```bash
   python manage.py createsuperuser
   ```

6. Run the development server:

   ```bash
   python manage.py runserver
   ```

7. Access the application in your web browser at http://localhost:8000.

8. Log in as the admin using the superuser account created in step 5 to access the admin dashboard.


## Behind the Scenes

### Student App

The Student app is used for authentication and includes student and department models. The Student model has fields for first+last name, department (a foreign key), and studentID (one-to-one field to Django's User model). Django's User Model is used for authentication.

### Library App

The Library app is the main app where the library system's logic is implemented. It includes the following models:

- **Author**: Stores the name and description of authors.
- **Book**: Stores the name, image, category of a book, and connects to the author.
- **Issue**: Tracks each student's issue requests, including book details, issue status, return status, return date, and more.
- **Fine**: Tracks fines and calculates fines automatically for students whose issued books are not returned.

## Important Logics

- **Student ID**: Username of Django's User Model serves as our studentID.
- **Signing Up**: Students who sign up create a new user instance with their student ID as the username, and a corresponding student instance is created with their names and department.
- **Calculating Fine**: Fines are calculated by looping through all the issues. For each issue, it checks whether the issue is issued, whether it's returned, and whether the return date has passed. If not, a fine is created or updated.

---
