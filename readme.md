Network

A Twitter-like social network built with Python, Django, JavaScript, HTML, and CSS.

Users can create posts, follow other users, like posts, edit their own posts, and browse personalized feeds.

Features

- User Authentication — Register, log in, and log out.
- Create Posts — Authenticated users can create text posts.
- Edit Posts — Users can edit their own posts.
- Like & Unlike — Users can like or unlike posts.
- User Profiles — View a user's posts, followers, and following count.
- Follow & Unfollow — Users can follow other users.
- Following Feed — View posts from users you follow.
- Pagination — Posts are displayed 10 per page.
- Dynamic Updates — JavaScript is used for likes and post editing without requiring a full page reload.

Technologies

- Python
- Django
- JavaScript
- HTML
- CSS
- SQLite

---

Django

Django is the backend framework used for this project.

It handles the main application logic, including:

- URL routing
- User authentication
- Creating and editing posts
- Following and unfollowing users
- Likes
- Database operations
- Rendering HTML templates
- Permissions and access control

The project is divided into a Django project and a Django application.

"project4/"

"project4" contains the main Django project configuration.

It is responsible for settings such as:

- Database configuration
- Installed applications
- URL configuration
- Static files
- Templates
- Middleware

"network/"

"network" is the main Django application.

It contains the functionality of the social network, such as:

- Posts
- Profiles
- Following
- Likes
- Authentication
- Feed functionality

In simple terms:

«"project4" configures the Django project, while "network" contains the actual social network functionality.»

---

How Django Works in This Project

When a user interacts with the website, the request is sent to Django.

Django determines which URL and view should handle the request. The view then communicates with the database using Django's ORM and returns the appropriate response.

For example, when loading the posts page:

1. The browser sends a request to Django.
2. Django matches the requested URL.
3. The appropriate view is called.
4. The view retrieves posts from the database.
5. Django renders the template.
6. The resulting HTML is sent back to the browser.

Django ORM

The project uses Django's Object-Relational Mapper (ORM) to communicate with the SQLite database.

The ORM allows the application to work with database records using Python instead of writing SQL queries directly.

The database stores information such as users, posts, likes, and relationships between users.

---

Django and JavaScript

Django handles the backend and database, while JavaScript is used to make the website more interactive.

For example, when a user likes a post, JavaScript sends a request to Django. Django updates the database and returns a response, and JavaScript updates the like information on the page.

The same approach is used when editing posts.

This allows users to interact with the website without having to reload the entire page after every action.

---

Project Structure

networkfinalllll/
│
├── network/              # Main Django application
├── project4/             # Django project configuration
├── static/               # Static files
├── db.sqlite3            # SQLite database
├── manage.py             # Django management utility
├── package.json          # JavaScript dependencies
├── package-lock.json     # Locked npm dependencies
└── requirements.txt      # Python dependencies

---

Running the Project

1. Clone the repository

git clone https://github.com/melinafallahpour/networkfinalllll.git
cd networkfinalllll

2. Install dependencies

pip install -r requirements.txt

3. Apply migrations

python manage.py makemigrations
python manage.py migrate

4. Run the development server

python manage.py runserver

Open the application at:

http://127.0.0.1:8000/

---

Live Website

"Visit the live website" (https://melinafp.pythonanywhere.com/)

---

Author

Melina Fallahpour

"GitHub" (https://github.com/melinafallahpour)
