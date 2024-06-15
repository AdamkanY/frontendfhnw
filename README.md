<!-- Improved compatibility of back to top link: See: https: https://github.com/AdamkanY/frontendfhnw/edit/main/README.md -->
<a name="readme-top"></a>






[![LinkedIn][linkedin-shield]][linkedin-url]
[![License](https://img.shields.io/:license-apache-blue.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)


<!-- PROJECT LOGO -->
<br />
<div align="center">
    <img src=https://asset.brandfetch.io/idJ2cw5Evl/idBPinAosj.jpeg alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">FHNW Community </h3>

  <p align="center">
    A awesome place to connect and grow into the FHNW Community!
    <br />
    <a href="https://github.com/AdamkanY/frontendfhnw/edit/main/README.md">View Demo</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#Overview">Overview</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
        <li><a href="#Technologies-Used">Technologies Used</a></li>
      </ul>
    </li>
    <li>
      <a href="#Pages">Navigate Pages</a>
      <ul>
        <li><a href="#Homepage">Homepage</a></li>
         <li><a href="#login">Login</a></li>
         <li><a href="#signup">Signup</a></li>
         <li><a href="#tutor-looking">Tutor-Looking</a></li>
         <li><a href="#user-dashboard">User Dashboard</a></li>
         <li><a href="#meet-a-tutor">Meet a Tutor</a></li>
         <li><a href="#create-advert-post">Create Advert Post</a></li>
      </ul>
    </li>
    <li><a href="#Back-end">Back-End</a></li>

  </ol>
</details>



<!-- Overview -->
## Overview
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/2ee0abd5-ebdb-485a-9f12-453f907c70db)



This repository contains the front-end code for the FHNW (Fachhochschule Nordwestschweiz) Community website. The website is designed to facilitate a vibrant community where students can connect with mentors, find study buddies, and access various resources to support their academic journey. The website includes the following pages:



Pages:
* Homepage
* Login
* Signup
* Tutor-Looking
* User Dashboard
* Meet a Tutor
* Create Advert Post
Wesbite link : https://communityfhnw.budibase.app/app/communityfhnw#/home-page

<p align="right">(<a href="#readme-top">back to top</a>)</p>



### Built With


![Budibase Badge](https://img.shields.io/badge/Budibase-000?logo=budibase&logoColor=fff&style=for-the-badge)

### Technologies Used 
* HTML5
* CSS3
* JavaScript

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- Pages -->
## Pages
### Homepage
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/7e882553-ded8-43a1-a0d9-851a9efdc38a)
### Homepage Part-2 
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/54002f22-40a3-4ef9-8fa6-7de2e2b819f1)

The homepage welcomes users with an engaging interface, highlighting the platform's purpose and providing quick access to join or log in.


### Login
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/7caf8f89-bb7a-496e-99ed-1ca53b4d6bb8)

The login page allows existing users to access their accounts by entering their username and password.


### Signup
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/baa333b3-6a8a-4ccc-85d9-46293b8f8273)

The signup page enables new users to create an account by providing their email and setting a password.


### User Dashboard
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/cf23de13-a17f-4713-8a11-5a96ab120bd0)

The user dashboard displays profile information and a list of upcoming tutoring sessions, allowing users to update their details and stay organized.



### Tutor-Looking
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/b66ac771-3114-4913-b89d-101a7834c719)

This page helps tutors find students based on various subjects and criteria, making it easy to connect with the right student.



### Meet a Tutor
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/d7a4468f-b7cd-4bf6-a4ce-5d42a18b9940)

Students can post if they are looking to meet a tutor

### Create Advert Post
![image](https://github.com/AdamkanY/frontendfhnw/assets/164184857/c837b484-4ab7-44a7-af3a-c961ccdcd79f)

The create advert post page allows users to create and publish advertisements for different purposes, facilitating easy communication and collaboration

<!-- ROADMAP -->
## Backend 

**Domain Model**
![Blank diagram](https://github.com/MateuszOskedraFHNWAccount/Internet-Technology/assets/164078789/08f9b726-46f9-48ae-8fc9-cfadd216f411)
<p align="right">(<a href="#readme-top">back to top</a>)</p>

**SQL**
![WhatsApp Image 2024-06-15 at 23 01 21_4d8ca785](https://github.com/AdamkanY/frontendfhnw/assets/164184857/229717cb-4681-4083-968a-b0999e5f971c)
```
-- Create sequences
CREATE SEQUENCE user_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE offer_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE project_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE post_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE response_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE log_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE ad_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE job_id_seq START WITH 1 INCREMENT BY 1;
CREATE SEQUENCE assignment_id_seq START WITH 1 INCREMENT BY 1;

-- Create Users table to store information about users
CREATE TABLE Users (
    user_id INT PRIMARY KEY,
    username VARCHAR2(50) NOT NULL UNIQUE,
    password_hash VARCHAR2(255) NOT NULL,
    email VARCHAR2(100) NOT NULL UNIQUE,
    role VARCHAR2(20) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Create trigger to set user_id using the sequence
CREATE OR REPLACE TRIGGER trg_users_user_id
BEFORE INSERT ON Users
FOR EACH ROW
BEGIN
    IF :new.user_id IS NULL THEN
        SELECT user_id_seq.NEXTVAL INTO :new.user_id FROM dual;
    END IF;
END;
/

-- Create TutoringOffers table for offering tutoring sessions
CREATE TABLE TutoringOffers (
    offer_id INT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR2(100) NOT NULL,
    description CLOB NOT NULL,
    recurring VARCHAR2(5) NOT NULL,
    timeline VARCHAR2(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- Create trigger to set offer_id using the sequence
CREATE OR REPLACE TRIGGER trg_tutoring_offers_offer_id
BEFORE INSERT ON TutoringOffers
FOR EACH ROW
BEGIN
    IF :new.offer_id IS NULL THEN
        SELECT offer_id_seq.NEXTVAL INTO :new.offer_id FROM dual;
    END IF;
END;
/

-- Create MentoringOffers table for offering mentoring sessions
CREATE TABLE MentoringOffers (
    offer_id INT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR2(100) NOT NULL,
    description CLOB NOT NULL,
    recurring VARCHAR2(5) NOT NULL,
    timeline VARCHAR2(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- Create trigger to set offer_id using the sequence
CREATE OR REPLACE TRIGGER trg_mentoring_offers_offer_id
BEFORE INSERT ON MentoringOffers
FOR EACH ROW
BEGIN
    IF :new.offer_id IS NULL THEN
        SELECT offer_id_seq.NEXTVAL INTO :new.offer_id FROM dual;
    END IF;
END;
/

-- Create IndependentProjects table for initiating independent projects
CREATE TABLE IndependentProjects (
    project_id INT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR2(100) NOT NULL,
    description CLOB NOT NULL,
    recurring VARCHAR2(5) NOT NULL,
    timeline VARCHAR2(50) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- Create trigger to set project_id using the sequence
CREATE OR REPLACE TRIGGER trg_independent_projects_project_id
BEFORE INSERT ON IndependentProjects
FOR EACH ROW
BEGIN
    IF :new.project_id IS NULL THEN
        SELECT project_id_seq.NEXTVAL INTO :new.project_id FROM dual;
    END IF;
END;
/

-- Create BuddyOffers table for volunteering as a buddy
CREATE TABLE BuddyOffers (
    offer_id INT PRIMARY KEY,
    user_id INT NOT NULL,
    languages VARCHAR2(100) NOT NULL,
    description CLOB NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- Create trigger to set offer_id using the sequence
CREATE OR REPLACE TRIGGER trg_buddy_offers_offer_id
BEFORE INSERT ON BuddyOffers
FOR EACH ROW
BEGIN
    IF :new.offer_id IS NULL THEN
        SELECT offer_id_seq.NEXTVAL INTO :new.offer_id FROM dual;
    END IF;
END;
/

-- Create RoomAssignments table for assigning rooms for events
CREATE TABLE RoomAssignments (
    assignment_id INT PRIMARY KEY,
    user_id INT NOT NULL,
    event_id INT,
    room_number VARCHAR2(20) NOT NULL,
    recurring VARCHAR2(5) NOT NULL,
    timeframe VARCHAR2(100) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- Create trigger to set assignment_id using the sequence
CREATE OR REPLACE TRIGGER trg_room_assignments_assignment_id
BEFORE INSERT ON RoomAssignments
FOR EACH ROW
BEGIN
    IF :new.assignment_id IS NULL THEN
        SELECT assignment_id_seq.NEXTVAL INTO :new.assignment_id FROM dual;
    END IF;
END;
/

-- Create ForumPosts table for forum posts
CREATE TABLE ForumPosts (
    post_id INT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR2(255) NOT NULL,
    content CLOB NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- Create trigger to set post_id using the sequence
CREATE OR REPLACE TRIGGER trg_forum_posts_post_id
BEFORE INSERT ON ForumPosts
FOR EACH ROW
BEGIN
    IF :new.post_id IS NULL THEN
        SELECT post_id_seq.NEXTVAL INTO :new.post_id FROM dual;
    END IF;
END;
/

-- Create ForumResponses table for forum responses
CREATE TABLE ForumResponses (
    response_id INT PRIMARY KEY,
    post_id INT NOT NULL,
    user_id INT NOT NULL,
    content CLOB NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (post_id) REFERENCES ForumPosts(post_id),
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- Create trigger to set response_id using the sequence
CREATE OR REPLACE TRIGGER trg_forum_responses_response_id
BEFORE INSERT ON ForumResponses
FOR EACH ROW
BEGIN
    IF :new.response_id IS NULL THEN
        SELECT response_id_seq.NEXTVAL INTO :new.response_id FROM dual;
    END IF;
END;
/

-- Create Logs table for storing access logs
CREATE TABLE Logs (
    log_id INT PRIMARY KEY,
    user_id INT NOT NULL,
    action VARCHAR2(100) NOT NULL,
    description CLOB,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

-- Create trigger to set log_id using the sequence
CREATE OR REPLACE TRIGGER trg_logs_log_id
BEFORE INSERT ON Logs
FOR EACH ROW
BEGIN
    IF :new.log_id IS NULL THEN
        SELECT log_id_seq.NEXTVAL INTO :new.log_id FROM dual;
    END IF;
END;
/

-- Create Advertisements table for posting advertisements
CREATE TABLE Advertisements (
    ad_id INT PRIMARY KEY,
    admin_id INT NOT NULL,
    title VARCHAR2(255) NOT NULL,
    content CLOB NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (admin_id) REFERENCES Users(user_id)
);

-- Create trigger to set ad_id using the sequence
CREATE OR REPLACE TRIGGER trg_advertisements_ad_id
BEFORE INSERT ON Advertisements
FOR EACH ROW
BEGIN
    IF :new.ad_id IS NULL THEN
        SELECT ad_id_seq.NEXTVAL INTO :new.ad_id FROM dual;
    END IF;
END;
/

-- Create JobAdvertisements table for posting job advertisements
CREATE TABLE JobAdvertisements (
    job_id INT PRIMARY KEY,
    admin_id INT NOT NULL,
    title VARCHAR2(255) NOT NULL,
    details CLOB NOT NULL,
    requirements CLOB NOT NULL,
    application_process CLOB NOT NULL,
    deadline TIMESTAMP NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (admin_id) REFERENCES Users(user_id)
);

-- Create trigger to set job_id using the sequence
CREATE OR REPLACE TRIGGER trg_job_advertisements_job_id
BEFORE INSERT ON JobAdvertisements
FOR EACH ROW
BEGIN
    IF :new.job_id IS NULL THEN
        SELECT job_id_seq.NEXTVAL INTO :new.job_id FROM dual;
    END IF;
END;
/

-- Create BuddyAssignments table for assigning buddies to international students
CREATE TABLE BuddyAssignments (
    assignment_id INT PRIMARY KEY,
    admin_id INT NOT NULL,
    international_student_id INT NOT NULL,
    buddy_id INT NOT NULL,
    assigned_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (admin_id) REFERENCES Users(user_id),
    FOREIGN KEY (international_student_id) REFERENCES Users(user_id),
    FOREIGN KEY (buddy_id) REFERENCES Users(user_id)
);

-- Create trigger to set assignment_id using the sequence
CREATE OR REPLACE TRIGGER trg_buddy_assignments_assignment_id
BEFORE INSERT ON BuddyAssignments
FOR EACH ROW
BEGIN
    IF :new.assignment_id IS NULL THEN
        SELECT assignment_id_seq.NEXTVAL INTO :new.assignment_id FROM dual;
    END IF;
END;
/

-- Create Roles table for storing user roles
CREATE TABLE Roles (
    role_id INT PRIMARY KEY,
    role_name VARCHAR2(20) NOT NULL
);

-- Insert initial roles into Roles table
INSERT INTO Roles (role_id, role_name) VALUES (1, 'Student');
INSERT INTO Roles (role_id, role_name) VALUES (2, 'Admin');
INSERT INTO Roles (role_id, role_name) VALUES (3, 'Super Admin');

-- Insert example data into Users table
INSERT INTO Users (username, password_hash, email, role) VALUES 
('Adam Kanouni', '12345678', 'adam.kanouni@students.fhnw.ch', 'Student');
INSERT INTO Users (username, password_hash, email, role) VALUES 
('Emirhan Akgun', '12345678', 'emirhan.akgun@students.fhnw.ch', 'Admin');
INSERT INTO Users (username, password_hash, email, role) VALUES 
('Mateusz Oskedra', '12345678', 'mateusz.oskedra@students.fhnw.ch', 'Super Admin');
INSERT INTO Users (username, password_hash, email, role) VALUES 
('Sina Najaflou', '12345678', 'sina.najaflou@students.fhnw.ch', 'Student');

-- Insert example data into JobAdvertisements table
INSERT INTO JobAdvertisements (admin_id, title, details, requirements, application_process, deadline) VALUES 
(2, 'Software Engineer', 'Develop software applications', 'BSc in Computer Science', 'Submit resume online', TO_TIMESTAMP('2023-12-31 23:59:59', 'YYYY-MM-DD HH24:MI:SS'));

-- Insert example data into TutoringOffers table
INSERT INTO TutoringOffers (user_id, title, description, recurring, timeline) VALUES 
(1, 'Math Tutoring', 'Tutoring for calculus and algebra', 'Yes', 'Weekly on Wednesdays');

-- Insert example data into MentoringOffers table
INSERT INTO MentoringOffers (user_id, title, description, recurring, timeline) VALUES 
(1, 'Career Mentoring', 'Mentoring for career development', 'No', 'Monthly on the first Monday');

-- Insert example data into IndependentProjects table
INSERT INTO IndependentProjects (user_id, title, description, recurring, timeline) VALUES 
(1, 'AI Research', 'Research on artificial intelligence', 'No', 'Throughout the semester');

-- Insert example data into BuddyOffers table
INSERT INTO BuddyOffers (user_id, languages, description) VALUES 
(1, 'English, Spanish', 'Buddy for international students');

-- Insert example data into RoomAssignments table
INSERT INTO RoomAssignments (user_id, event_id, room_number, recurring, timeframe) VALUES 
(1, 101, 'A101', 'Yes', 'Weekly on Tuesdays');

-- Insert example data into ForumPosts table
INSERT INTO ForumPosts (user_id, title, content) VALUES 
(1, 'Welcome to the Forum', 'Feel free to discuss any topics here.');

-- Insert example data into ForumResponses table
INSERT INTO ForumResponses (post_id, user_id, content) VALUES 
(1, 2, 'Thank you! Looking forward to it.');

-- Insert example data into Logs table
INSERT INTO Logs (user_id, action, description) VALUES 
(1, 'LOGIN', 'User logged in successfully.');

-- Insert example data into Advertisements table
INSERT INTO Advertisements (admin_id, title, content) VALUES 
(2, 'Spring Sale', 'Get discounts on all courses this spring!');

-- Insert example data into BuddyAssignments table
INSERT INTO BuddyAssignments (admin_id, international_student_id, buddy_id) VALUES 
(2, 1, 2);

```


<p align="right">(<a href="#readme-top">back to top</a>)</p>


#### License

[Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/kanouni-adam/
