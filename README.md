                                       #Task-4(Aggregate Functions and Grouping)

# 📚 College Management System Database
This project demonstrates how to design and implement a relational database schema for a College Management System using SQL. It includes the Insertion, Updating and deleting of a data.

# 🔍 Project Overview
This database system is designed to manage:

- Applying aggregate functions on numeric columns.
- Using GROUP BY to categorize the data.
- Using HAVING to filters the group.
  
The goal is to build a well-structured, normalized schema using SQL with aggregate functions.

This project is part of my learning and internship submission, aimed at demonstrating my understanding of database design concepts.

# 📌 Tables:

- Students
- Courses
- Enrollments

# SQL Script

Creating the data
```
-- Create the database
CREATE DATABASE College;
USE College;

-- Create Students table
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(60) UNIQUE,
    DOB DATE
);

-- Create Courses table
CREATE TABLE Courses (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(50) NOT NULL,
    Credits INT CHECK (Credits > 0)
);

-- Create Enrollments table
CREATE TABLE Enrollments (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    EnrollmentDate DATE,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
);
```

Inserting the data
```
--Inserting the data in Student table

Insert into students (StudentID, Name, Email,DOB) 
values (1,'Zanib Khan', 'zanib9482@gmail.com','2003-07-12'),
(2,'Kajal Patel','kajal2345@gmail.com','2002-07-20');

--Inserting the data in Courses table

Insert into Courses(CourseID,CourseName,Credits)
values(201,'Web Development',8),
(202,'SQL Developer',9);

--Inserting the data in Enrollment table

Insert into Enrollments(EnrollmentID,StudentID,CourseID,EnrollmentDate)
values(2001,1,202,'2025-06-23'),
(2002,2,201,'2025-06-12');
```

# Using Aggregate Functions
```
select count(*) as TotalStudents from students;
```
```
select max(Credits) as MaxCredits from Courses;
```

# Using Group By
```
select CourseID, Count(*) as EnrolledStudents from Enrollments Group By CourseID;
```

# Using Having Functions

```
select EnrollmentDate, Count(*) as TotaEnrollments from Enrollments Group By EnrollmentDate Having Count(*)<2;
```
