# SQL-ödevleri
1. Members
CREATE TABLE Members (
    member_id SERIAL PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    register_date TIMESTAMP NOT NULL,
    name VARCHAR(50),
    surname VARCHAR(50)


2. Courses
CREATE TABLE Courses (
    course_id SERIAL PRIMARY KEY,
    course_name VARCHAR(200) NOT NULL,
    description TEXT,
    start_date DATE,
    end_date DATE,
    instructor_info VARCHAR(100)

3. Categories
CREATE TABLE Categories (
    category_id SERIAL PRIMARY KEY,
    category_name VARCHAR(100) NOT NULL,
    sub_category VARCHAR(100)


4. CourseCategories (Çok-çok ilişkiyi yöneten tablo)
CREATE TABLE CourseCategories (
    course_id INTEGER REFERENCES Courses(course_id),
    category_id INTEGER REFERENCES Categories(category_id),
    PRIMARY KEY (course_id, category_id)


5. Enrollments
CREATE TABLE Enrollments (
    enrollment_id SERIAL PRIMARY KEY,
    member_id INTEGER REFERENCES Members(member_id),
    course_id INTEGER REFERENCES Courses(course_id),
    enrollment_date TIMESTAMP NOT NULL

6. Certificates
CREATE TABLE Certificates (
    certificate_id SERIAL PRIMARY KEY,
    certificate_code VARCHAR(100) UNIQUE NOT NULL,
    issue_date DATE,
    certificate_info TEXT


7. CertificateAssignments
CREATE TABLE CertificateAssignments (
    member_id INTEGER REFERENCES Members(member_id),
    course_id INTEGER REFERENCES Courses(course_id),
    certificate_id INTEGER REFERENCES Certificates(certificate_id),
    PRIMARY KEY (member_id, course_id, certificate_id)

8. BlogPosts
CREATE TABLE BlogPosts (
    post_id SERIAL PRIMARY KEY,
    member_id INTEGER REFERENCES Members(member_id),
    title VARCHAR(255),
    content TEXT,
    post_date TIMESTAMP NOT NULL

