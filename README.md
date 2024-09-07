CREATE DATABASE EmployeeManagement;
USE EmployeeManagement;
CREATE TABLE Employee (
    EmployeeID INT PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Gender CHAR(1),
    DateOfBirth DATE,
    HireDate DATE,
    DepartmentID INT,
    JobID INT,
    FOREIGN KEY (DepartmentID) REFERENCES Department(DepartmentID),
    FOREIGN KEY (JobID) REFERENCES Job(JobID)
);
CREATE TABLE Department (
    DepartmentID INT PRIMARY KEY AUTO_INCREMENT,
    DepartmentName VARCHAR(100) NOT NULL,
    ManagerID INT,
    FOREIGN KEY (ManagerID) REFERENCES Employee(EmployeeID)
);
CREATE TABLE Job (
    JobID INT PRIMARY KEY AUTO_INCREMENT,
    JobTitle VARCHAR(100) NOT NULL,
    MinSalary DECIMAL(10, 2),
    MaxSalary DECIMAL(10, 2)
);
CREATE TABLE Salary (
    SalaryID INT PRIMARY KEY AUTO_INCREMENT,
    EmployeeID INT,
    SalaryAmount DECIMAL(10, 2) NOT NULL,
    EffectiveDate DATE NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employee(EmployeeID)
);
INSERT INTO Job (JobTitle, MinSalary, MaxSalary) VALUES
('Software Engineer', 60000, 120000),
('Data Analyst', 50000, 100000),
('HR Manager', 70000, 150000),
('Marketing Manager', 75000, 140000);
INSERT INTO Department (DepartmentName, ManagerID) VALUES
('IT', 1),
('HR', 2),
('Marketing', 3),
('Finance', 4);
INSERT INTO Employee (FirstName, LastName, Gender, DateOfBirth, HireDate, DepartmentID, JobID) VALUES
('John', 'Doe', 'M', '1990-01-15', '2018-06-23', 1, 1),
('Jane', 'Smith', 'F', '1988-03-22', '2017-04-15', 2, 3),
('Robert', 'Brown', 'M', '1992-05-10', '2019-07-10', 3, 4),
('Emily', 'Johnson', 'F', '1985-12-05', '2016-01-20', 1, 2);
INSERT INTO Salary (EmployeeID, SalaryAmount, EffectiveDate) VALUES
(1, 85000, '2018-06-23'),
(2, 90000, '2017-04-15'),
(3, 100000, '2019-07-10'),
(4, 70000, '2016-01-20');
SELECT e.EmployeeID, e.FirstName, e.LastName, d.DepartmentName, j.JobTitle
FROM Employee e
JOIN Department d ON e.DepartmentID = d.DepartmentID
JOIN Job j ON e.JobID = j.JobID;

SELECT e.EmployeeID, e.FirstName, e.LastName, d.DepartmentName, j.JobTitle
FROM Employee e
JOIN Department d ON e.DepartmentID = d.DepartmentID
JOIN Job j ON e.JobID = j.JobID;
SELECT d.DepartmentName, AVG(s.SalaryAmount) AS AverageSalary
FROM Employee e
JOIN Salary s ON e.EmployeeID = s.EmployeeID
JOIN Department d ON e.DepartmentID = d.DepartmentID
GROUP BY d.DepartmentName;
SELECT e.FirstName, e.LastName, s.SalaryAmount, s.EffectiveDate
FROM Employee e
JOIN Salary s ON e.EmployeeID = s.EmployeeID
ORDER BY e.EmployeeID, s.EffectiveDate;
SELECT e.FirstName, e.LastName, MAX(s.SalaryAmount) AS HighestSalary
FROM Employee e
JOIN Salary s ON e.EmployeeID = s.EmployeeID
GROUP BY e.EmployeeID
ORDER BY HighestSalary DESC
LIMIT 1;








