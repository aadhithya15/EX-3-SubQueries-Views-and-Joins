# EX 3 SubQueries, Views and Joins 

## Aim:
To view implement Subqueries , views and joins.

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
```sql
SELECT ename FROM EMP WHERE sal > (SELECT sal FROM EMP WHERE empno = 7566);
```
### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/150aa9ea-6214-488b-8019-2366a991aa30)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
```sql
SELECT ename,job,sal FROM EMP WHERE sal = (SELECT MIN(sal) FROM EMP);
```

### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/270fa305-96b6-4855-a9b8-873ecb5cfbcf)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```sql
SELECT ename,job FROM EMP WHERE deptno = 10 AND job IN (SELECT job FROM EMP WHERE job = 'sales');
```

### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/3b950a26-e4d9-41ce-80fc-f567a6bcc18d)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```sql
create view empv5 as select EMPNO,ENAME,JOB from EMP where DEPTNO=10;
SELECT * FROM empv5;
```

### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/429d6a5f-5ca6-4356-a1f8-94a781b1ee8f)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```sql
create view empv30 AS select EMPNO,ENAME,SAL from EMP where DEPTNO=30;
SELECT * FROM empv30;
```

### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/1f2c0f0f-3b00-4d7f-8467-cad5a99f22c1)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```sql
UPDATE EMP SET sal = sal * 1.1 WHERE job = 'CLERK';
create view empv5 as select EMPNO,ENAME,SALARY,JOB from EMP;
```

### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/0d4e2684-9bbc-4ad5-945b-e9109417e371)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
```sql
select s.name,c.cust_name,s.city from salesman1 s ,customer1 c where s.city=c.city;
```

### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/ad5ec773-b492-4e76-bae4-8334bc4b825d)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
```sql
select s.name,c.cust_name,c.city,s.commission from salesman1 s inner join customer1 c on s.city=c.city where s.commission>0.13;
```

### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/3dc1ee76-fbc4-4ca6-86d7-41520dcbd3b0)

### Q9) Perform Natural join on both tables

### QUERY:
```sql
 select * from salesman1 s natural join customer1 c;
```

### OUTPUT:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/acad8088-4f89-4ec6-a116-928c23ab54b3)

### Q10) Perform Left and right join on both tables

### QUERY:
```sql
select s.name,c.cust_name,c.city,s.commission from salesman1 s left join customer1 c on s.salesman_id=c.salesman_id;

select s.name,c.cust_name,c.city,s.commission from salesman1 s right join customer1 c on s.salesman_id=c.salesman_id;
```


### OUTPUT:
### Left Joint:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/ed2e300d-272b-42cb-84f6-2d7a34fe8574)

### Right Joint:
![image](https://github.com/KothaiKumar/EX-3-SubQueries-Views-and-Joins/assets/121215739/489efc4b-710d-40f4-834d-337f6860d219)

### Result:
A database is created and views , subqueries and joins are executed successfully . 
