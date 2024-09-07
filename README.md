Employee Management System

Project Overview:
The goal of this project is to design and implement an employee management system using SQL. The system will manage data for employees, departments, and job roles, with features for managing employee records, querying for performance, and analyzing department data.

Database Design:
Entities and Relationships:
Employee: Stores personal and employment-related data.
Department: Stores information about departments in the company.
Job: Stores job roles and titles.
Salary: Tracks salary changes and history for employees.

Schema Diagram:
Employee (EmployeeID, FirstName, LastName, Gender, DateOfBirth, HireDate, DepartmentID, JobID)
Department (DepartmentID, DepartmentName, ManagerID)
Job (JobID, JobTitle, MinSalary, MaxSalary)
Salary (SalaryID, EmployeeID, SalaryAmount, EffectiveDate)








