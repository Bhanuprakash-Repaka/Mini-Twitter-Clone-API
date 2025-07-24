# Twitter Clone Backend API

This is a lightweight backend API that simulates core functionalities of Twitter using *Node.js, **Express.js, **SQLite, and **JWT authentication*. It handles user registration, login, tweet creation, following users, viewing tweets, likes, replies, and more.

## 📁 Tables in Database (twitterClone.db)
The backend operates on five main database tables:

1. *User*
   - user_id, name, username, password, gender
2. *Follower*
   - follower_id, follower_user_id, following_user_id
3. *Tweet*
   - tweet_id, tweet, user_id, date_time
4. *Reply*
   - reply_id, tweet_id, reply, user_id, date_time
5. *Like*
   - like_id, tweet_id, user_id, date_time

---

## 🔐 Authentication

JWT is used to protect the APIs. Users must log in to receive a token which is then used in all protected routes.

### Middleware

Handles token validation:

- If token is missing or invalid → 401 Invalid JWT Token
- On success → proceeds to next handler

---

## 🛠 API Endpoints

### 🔹 API 1: Register
- *Path*: /register/
- *Method*: POST
- *Scenarios*:
  - Username exists → 400 User already exists
  - Password < 6 chars → 400 Password is too short
  - Success → 200 User created successfully

### 🔹 API 2: Login
- *Path*: /login/
- *Method*: POST
- *Scenarios*:
  - Invalid user → 400 Invalid user
  - Wrong password → 400 Invalid password
  - Success → returns JWT token

---

### 🟩 Protected Routes (JWT Required)

#### 🔸 API 3: Get Feed Tweets
- *Path*: /user/tweets/feed/
- *Method*: GET
- *Returns*: Latest 4 tweets of followed users

#### 🔸 API 4: Get Following List
- *Path*: /user/following/
- *Method*: GET
- *Returns*: Names of people the user follows

#### 🔸 API 5: Get Followers List
- *Path*: /user/followers/
- *Method*: GET
- *Returns*: Names of users who follow the user

#### 🔸 API 6: Get Specific Tweet
- *Path*: /tweets/:tweetId/
- *Method*: GET
- *If unauthorized*: 401 Invalid Request
- *Returns*: Tweet, likes, replies, and dateTime

#### 🔸 API 7: Get Tweet Likes
- *Path*: /tweets/:tweetId/likes/
- *Method*: GET
- *If unauthorized*: 401 Invalid Request
- *Returns*: List of usernames who liked the tweet

#### 🔸 API 8: Get Tweet Replies
- *Path*: /tweets/:tweetId/replies/
- *Method*: GET
- *If unauthorized*: 401 Invalid Request
- *Returns*: List of replies

#### 🔸 API 9: Get User Tweets
- *Path*: /user/tweets/
- *Method*: GET
- *Returns*: All tweets by the logged-in user

#### 🔸 API 10: Create Tweet
- *Path*: /user/tweets/
- *Method*: POST
- *Creates*: A tweet entry in the database

#### 🔸 API 11: Delete Tweet
- *Path*: /tweets/:tweetId/
- *Method*: DELETE
- *If unauthorized*: 401 Invalid Request
- *If own tweet*: Tweet Removed

---

### 🔧Tech Stack 
Node.js
Express.js
SQLite
JWT (jsonwebtoken)
Bcrypt.js

---

### 🚀Future Enhancements

Add frontend interface for user interaction

Support media uploads in tweets

Implement search and pagination

Migrate database to PostgreSQL

Improve security and error handling

Deploy API to cloud platform
