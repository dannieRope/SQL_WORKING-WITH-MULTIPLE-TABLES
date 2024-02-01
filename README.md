# SQL_WORKING-WITH-MULTIPLE-TABLES
                              WORKING WITH MULTIPLE TABLES
```sql
---Retrieve only the Employees records that correspond to jobs in the jobs table
SELECT *
FROM Employees
WHERE job_id IN (SELECT job_ident
                 FROM Jobs);

---Retrieve only the list of employees whose JOB_TITLE is Jr. Designer.
SELECT *
FROM Employees E
INNER JOIN  Jobs J
ON E.job_id = J.job_ident
WHERE job_title = 'Jr. Designer';

SELECT *
FROM Employees
WHERE job_id IN (SELECT job_ident
                 FROM Jobs
				 WHERE job_title = 'Jr. Designer');

---Retrieve JOB information and who earn more than $70000
SELECT *
FROM Jobs 
WHERE job_ident IN (SELECT job_id
					FROM Employees
					WHERE salary>70000);

---Retrieve JOB information and whose birth year after 1976.
SELECT *
FROM Jobs
WHERE job_ident IN (SELECT job_id
                    FROM Employees
					WHERE YEAR(b_date)> 1976);

---Perform implicit cartesian/cross join between employees and jobs tables
SELECT *
FROM employees E, Jobs J;

---Retrieve only the employees records that correspond to jobs in the JObs table
SELECT *
FROM Employees E ,Jobs J
WHERE E.job_id = J.job_ident;

---Redo the previous query, but retrieve only the employee ID, employee name and job title
SELECT E.emp_id,
       E.f_name,
	   E.l_name,
	   J.job_title
FROM Employees E ,Jobs J
WHERE E.job_id = J.job_ident;
```

