# melinafallahpour

🌐 Network — Social Network Web Application

A modern Twitter-like social networking website built with Django, Python, JavaScript, HTML, and CSS.

The application allows users to create posts, follow other users, like posts, edit their own content, and browse personalized feeds.

🔗 Live Demo: "Network" (https://melinafp.pythonanywhere.com/)

🎥 Video Demo: "Watch the Demo" (https://youtu.be/)

---

✨ Features

👤 User Authentication

- User registration and login
- Secure session-based authentication
- Users can only access authenticated features when signed in

📝 Posts

- Create text-based posts
- View posts from all users
- Posts are displayed in reverse chronological order
- Edit your own posts
- Users cannot edit posts created by other users

❤️ Likes

- Like and unlike posts
- Like counts update dynamically
- JavaScript communicates with the Django backend without requiring a full page reload

👥 Following System

- Follow other users
- Unfollow users
- View follower and following counts
- Users cannot follow themselves
- Personalized Following feed showing posts from followed users

👤 User Profiles

Each profile displays:

- Username
- Number of followers
- Number of users being followed
- Posts created by the user
- Follow / Unfollow functionality

📄 Pagination

Posts are displayed 10 at a time.

When additional posts are available, users can navigate using:

- Next
- Previous

This keeps pages easier to browse and prevents large numbers of posts from being loaded at once.

⚡ Dynamic Interactions

JavaScript is used for actions that don't require a complete page refresh, including:

- Editing posts
- Liking and unliking posts
- Updating information displayed on the page

---

🛠️ Technology Stack

Technology| Purpose
Python| Main programming language
Django| Backend web framework
JavaScript| Dynamic client-side interactions
HTML| Page structure
CSS| Styling and layout
SQLite| Development database
Node.js / npm| Front-end package management

---

🐍 How Django Is Used

Django is the main backend framework of this application.

Instead of having JavaScript directly manage the database, Django sits between the website and the database and handles the application's core logic.

The project follows Django's typical structure, with the "network" directory acting as the main application and "project4" containing the project-level configuration.

A simplified architecture looks like this:

                ┌─────────────────────┐
                │      Browser        │
                │ HTML / CSS / JS     │
                └──────────┬──────────┘
                           │
                     HTTP Requests
                           │
                           ▼
                ┌─────────────────────┐
                │       Django        │
                │      Backend        │
                └──────────┬──────────┘
                           │
              ┌────────────┼────────────┐
              │            │            │
              ▼            ▼            ▼
           URLs         Views        Models
              │            │            │
              │            │            ▼
              │            │        Database
              │            │
              └────────────┴──► Templates

Django's role

Django is responsible for:

1. Receiving requests from the browser
2. Determining which URL was requested
3. Running the appropriate view
4. Reading or modifying data through Django's ORM
5. Checking authentication and permissions
6. Rendering HTML templates
7. Returning responses to the browser
8. Providing data to JavaScript when asynchronous requests are made

---

🧱 Django Project Structure

The repository contains two important Django directories:

networkfinalllll/
│
├── network/
│   └── ...              # Main Django application
│
├── project4/
│   └── ...              # Django project configuration
│
├── static/
│   └── ...              # Static files
│
├── db.sqlite3           # SQLite database
├── manage.py             # Django command-line utility
├── requirements.txt      # Python dependencies
│
├── package.json          # JavaScript dependencies
└── package-lock.json

"project4/"

This is the Django project configuration.

It contains the settings and configuration that tell Django how the entire website should operate.

For example, Django uses the project configuration to determine things such as:

- Installed applications
- Database configuration
- URL configuration
- Static files
- Templates
- Middleware
- Authentication configuration

"network/"

This is the main Django application.

It contains the functionality specific to the social network, such as:

- Posts
- Users
- Following
- Likes
- Profiles
- Feed functionality

This separation is important in Django:

«The project ("project4") configures the website, while the app ("network") implements the website's functionality.»

---

🔄 How a Request Works

For example, when a user opens the All Posts page:

User
 │
 │ GET request
 ▼
Django URL configuration
 │
 ▼
Network view
 │
 ▼
Django ORM
 │
 ▼
Database
 │
 ▼
Posts returned
 │
 ▼
Django template
 │
 ▼
HTML response
 │
 ▼
Browser

The Django ORM (Object-Relational Mapper) allows Python code to work with database records without manually writing SQL for every operation.

Conceptually, instead of directly writing SQL such as:

SELECT * FROM posts;

Django allows application code to work with database objects through its model/query system.

This makes it easier to retrieve, create, update, and filter application data.

---

⚡ Django + JavaScript

One of the important parts of this project is that Django doesn't have to reload the entire page for every action.

For example, when a user likes a post:

User clicks "Like"
        │
        ▼
JavaScript event
        │
        ▼
Asynchronous request
        │
        ▼
Django backend
        │
        ▼
Database updated
        │
        ▼
Django sends response
        │
        ▼
JavaScript updates like count
        │
        ▼
Page stays loaded

The project specification specifically requires likes and post editing to communicate with the backend asynchronously, allowing the interface to update without a full page reload.

This creates a more responsive user experience while Django remains responsible for the actual data and business logic.

---

🗃️ Database

The project includes a SQLite database:

db.sqlite3

The database stores persistent application information such as users, posts, relationships between users, and likes.

Django's ORM provides the layer between Python/Django code and SQLite.

Conceptually:

Django Models
      │
      ▼
Django ORM
      │
      ▼
SQLite
      │
      ▼
db.sqlite3

SQLite is convenient for development and small projects because it does not require a separate database server.

---

🔐 Authentication & Permissions

Django's authentication system is used to distinguish between signed-in and anonymous users.

This is particularly important for operations such as:

- Creating posts
- Editing posts
- Following users
- Liking posts
- Viewing the Following feed

The application also needs to enforce ownership rules on the backend.

For example:

User A
  │
  ├── owns Post 1
  │
  └── can edit Post 1

User B
  │
  └── cannot edit Post 1

This is enforced by Django rather than relying only on hiding an Edit button in the browser.

---

📄 Pagination

The application uses pagination for pages containing posts.

Instead of displaying every post at once:

Page 1 → Posts 1–10
Page 2 → Posts 11–20
Page 3 → Posts 21–30

The project specification requires ten posts per page, with navigation to older and newer pages when appropriate.

Django's pagination functionality can handle this efficiently on the backend.

---

🚀 Getting Started

1. Clone the repository

git clone https://github.com/melinafallahpour/networkfinalllll.git
cd networkfinalllll

2. Create a virtual environment

Windows

python -m venv venv
venv\Scripts\activate

macOS / Linux

python3 -m venv venv
source venv/bin/activate

3. Install Python dependencies

pip install -r requirements.txt

4. Apply Django migrations

python manage.py makemigrations
python manage.py migrate

5. Start the development server

python manage.py runserver

The application will normally be available at:

http://127.0.0.1:8000/

---

📦 Project Dependencies

Python dependencies are listed in:

requirements.txt

JavaScript dependencies are managed through:

package.json
package-lock.json

This project therefore combines a Python/Django backend with client-side JavaScript functionality.

---

🎯 Project Goals

This project demonstrates how a full-stack web application can be built using Django while combining server-side functionality with client-side JavaScript.

The main concepts demonstrated include:

- Django project/app architecture
- URL routing
- Views
- Models and ORM
- Database relationships
- Authentication
- Authorization
- Templates
- Static files
- JavaScript event handling
- Asynchronous requests
- Pagination
- Social relationships between users

---

📚 Learning Outcomes

Building this application provides practical experience with the complete request/response cycle:

Frontend
   ↓
HTTP Request
   ↓
Django URL
   ↓
Django View
   ↓
Django ORM
   ↓
Database
   ↓
Django Response
   ↓
Frontend

It also demonstrates how a traditional Django-rendered application can be enhanced with JavaScript to provide dynamic interactions without turning the entire application into a separate frontend framework.

---

👩‍💻 Author

Melina Fallahpour

GitHub: "@melinafallahpour" (https://github.com/melinafallahpour)

---

📄 License

This project was created as a web development project for learning and demonstrating Django, JavaScript, and full-stack web development.
