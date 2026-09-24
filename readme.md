🌐 Network

A Twitter-like social network built with Python, Django, JavaScript, HTML, and CSS.

Users can create posts, follow other users, like and unlike posts, edit their own posts, and browse personalized feeds.

🔗 Live Site

"Visit the live website" (https://melinafp.pythonanywhere.com/)

🎥 Video Demo

"Watch the video demonstration" (https://youtu.be/)

---

✨ Features

👤 Authentication

- User registration and login
- Session-based authentication
- Different functionality for authenticated and anonymous users

📝 Posts

- Create text posts
- View posts from all users
- Posts are displayed in reverse chronological order
- Edit your own posts
- Users cannot edit posts created by other users

❤️ Likes

- Like and unlike posts
- Like counts are updated dynamically
- JavaScript communicates with Django asynchronously

👥 Following

- Follow other users
- Unfollow users
- View follower and following counts
- Users cannot follow themselves
- Personalized Following feed

👤 Profiles

Each profile displays:

- Username
- Number of followers
- Number of people being followed
- Posts created by the user
- Follow / Unfollow functionality

📄 Pagination

Posts are displayed 10 per page.

Users can navigate between pages using:

- Previous
- Next

⚡ Dynamic Interactions

JavaScript is used to make parts of the application interactive without requiring a complete page reload.

This includes:

- Editing posts
- Liking and unliking posts
- Updating information displayed on the page

---

🛠️ Technologies

Technology| Purpose
Python| Backend programming
Django| Web framework and backend
JavaScript| Dynamic client-side interactions
HTML| Page structure
CSS| Styling
SQLite| Database
npm| JavaScript package management

---

🐍 Django Backend

Django is the main backend framework of the application.

It is responsible for handling the application's URLs, views, database operations, authentication, permissions, and HTML rendering.

The browser communicates with Django through HTTP requests.

flowchart TD
    A[User] --> B[Browser]
    B -->|HTTP Request| C[Django]
    C --> D[URL Routing]
    D --> E[View]
    E --> F[Django ORM]
    F --> G[(SQLite Database)]
    G --> F
    F --> E
    E --> H[Template]
    H --> B

Django acts as the connection between the frontend and the database.

---

🧱 Django Project Structure

The project contains two important Django components:

networkfinalllll/
│
├── network/
├── project4/
├── static/
├── manage.py
├── db.sqlite3
├── package.json
├── package-lock.json
└── requirements.txt

"project4/"

"project4" is the Django project configuration.

It contains the configuration required to run the website, including settings and the project's main URL configuration.

In simple terms:

«"project4" configures the Django project.»

"network/"

"network" is the main Django application.

It contains the functionality of the social network, including:

- Posts
- Profiles
- Following
- Likes
- Authentication
- Feed functionality
- Post editing

The relationship between the project and application can be represented as:

flowchart LR
    A[project4<br/>Django Project] --> B[network<br/>Django App]
    B --> C[Social Network Features]
    C --> D[Posts]
    C --> E[Profiles]
    C --> F[Following]
    C --> G[Likes]

---

🔄 Request & Response Flow

For example, when a user visits the All Posts page, the request follows Django's request/response cycle.

sequenceDiagram
    participant U as User
    participant B as Browser
    participant D as Django
    participant V as View
    participant DB as SQLite

    U->>B: Open All Posts
    B->>D: GET request
    D->>V: Route request
    V->>DB: Request posts
    DB-->>V: Return posts
    V-->>D: Render template
    D-->>B: HTML response
    B-->>U: Display posts

Django receives the request, determines which view should handle it, retrieves the required information from the database, renders the appropriate template, and returns the resulting HTML to the browser.

---

🗃️ Django ORM

The application uses Django's Object-Relational Mapper (ORM) to communicate with the database.

The ORM allows Python and Django code to interact with database records without manually writing SQL for every operation.

The relationship looks like this:

flowchart TD
    A[Django Application] --> B[Django Models]
    B --> C[Django ORM]
    C --> D[(SQLite)]
    D --> E[db.sqlite3]

The database is used to persist information such as users, posts, likes, and relationships between users.

---

⚡ Django + JavaScript

Django handles the backend logic, while JavaScript provides dynamic interactions in the browser.

For example, when a user likes a post:

sequenceDiagram
    participant U as User
    participant JS as JavaScript
    participant D as Django
    participant DB as Database

    U->>JS: Click Like
    JS->>D: Asynchronous request
    D->>DB: Update like
    DB-->>D: Updated data
    D-->>JS: Response
    JS-->>U: Update like count

The entire page does not need to reload.

The same approach is used when editing posts.

This creates a more responsive interface while Django remains responsible for the application's logic and database operations.

---

🔐 Authentication & Permissions

Django's authentication system is used to determine whether a user is signed in and what actions they are allowed to perform.

For example:

flowchart TD
    A[User] --> B{Authenticated?}

    B -->|No| C[Public Pages]
    B -->|Yes| D[Authenticated Features]

    D --> E[Create Post]
    D --> F[Like Post]
    D --> G[Follow Users]
    D --> H[View Following Feed]
    D --> I[Edit Own Posts]

The application also checks ownership when editing posts.

A user can edit their own post, but another user cannot edit it.

flowchart LR
    A[User] --> B{Owns Post?}
    B -->|Yes| C[Allow Editing]
    B -->|No| D[Reject Editing]

This type of permission is enforced by the backend rather than relying only on hiding an Edit button in the browser.

---

👥 Following System

The following system creates relationships between users.

flowchart LR
    A[User A] -->|Follows| B[User B]
    A -->|Follows| C[User C]

    B --> D[Posts]
    C --> E[Posts]

    D --> F[Following Feed]
    E --> F

The Following page uses these relationships to display posts from users that the current user follows.

---

❤️ Like System

Likes connect users with posts.

flowchart TD
    A[User] -->|Likes| B[Post]
    B --> C[Like Count]

    A -->|Unlikes| B
    B --> C

JavaScript allows the like state and count to be updated dynamically without reloading the entire page.

---

📄 Pagination

Posts are divided into pages containing 10 posts.

flowchart LR
    A[All Posts] --> B[Page 1<br/>Posts 1-10]
    A --> C[Page 2<br/>Posts 11-20]
    A --> D[Page 3<br/>Posts 21-30]

    B <-->|Next / Previous| C
    C <-->|Next / Previous| D

Pagination keeps the interface manageable when there are many posts.

---

📁 Project Structure

networkfinalllll/
│
├── network/              # Main Django application
│
├── project4/             # Django project configuration
│
├── static/               # Static files
│
├── 1.jpg                 # Project image
│
├── db.sqlite3            # SQLite database
│
├── manage.py             # Django management utility
│
├── package.json          # JavaScript dependencies
│
├── package-lock.json     # Locked npm dependencies
│
└── requirements.txt      # Python dependencies

---

🚀 Running the Project Locally

1. Clone the repository

git clone https://github.com/melinafallahpour/networkfinalllll.git
cd networkfinalllll

2. Install Python dependencies

pip install -r requirements.txt

3. Apply migrations

python manage.py makemigrations
python manage.py migrate

4. Start the Django development server

python manage.py runserver

The website will then be available at:

http://127.0.0.1:8000/

---

🎯 What This Project Demonstrates

This project demonstrates the development of a full-stack web application using Django.

Key concepts include:

- Django project and app architecture
- URL routing
- Views
- Templates
- Django ORM
- SQLite
- Authentication
- Authorization
- User relationships
- Pagination
- JavaScript
- Asynchronous requests
- Dynamic page updates

The overall architecture can be summarized as:

flowchart TD
    A[Frontend<br/>HTML + CSS + JavaScript]
    B[Django Backend]
    C[Views]
    D[Models + ORM]
    E[(SQLite Database)]

    A -->|HTTP Requests| B
    B --> C
    C --> D
    D --> E
    E --> D
    D --> C
    C --> B
    B -->|HTML / JSON Response| A

Django therefore provides the core backend architecture, while JavaScript enhances the frontend with dynamic interactions.

---

👩‍💻 Author

Melina Fallahpour

"GitHub Profile" (https://github.com/melinafallahpour)
