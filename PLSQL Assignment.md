// PL/SQL Basics...

 SQL> set lines 120 pages 120;
SQL> declare
  2  a number(3):= 100;
  3  begin
  4  dbms_output.put_line('values of a is '||a);
  5  end;
  6  /

PL/SQL procedure successfully completed.

SQL> set serveroutput on;
SQL>     declare
  2      a number(3):= 100;
  3      begin
  4      dbms_output.put_line('values of a is '||a);
  5      end;
  6      /
values of a is 100

PL/SQL procedure successfully completed.

SQL> declare
  2  msg varchar(10);
  3  begin
  4  msg:='shivprasad';
  5  dbms_output.put_line('my name is :'|| msg);
  6  end;
  7  /
my name is :shivprasad

PL/SQL procedure successfully completed.

SQL>set lines 120 pages 120;

 1) Write a PL/SQL block to retrieve the employee name, job title, and salary for the employee with EMPNO 7839.
SQL> declare
    name varchar(10);
    job varchar(10);
    sal number(10);
    begin
    select ename,job,sal into name,job,sal from emp
    where empno = 7839;
    dbms_output.put_line('Employee name is :'|| name);
    dbms_output.put_line('Employee job is :'|| job);
    dbms_output.put_line('Employee sla is :'|| sal);
    end;
    /

2) Develop a PL/SQL block to fetch the employee number, name, and department number for the employee whose salary exceeds 2000, job designation contains 'MAN', and who belongs to department 10.

SQL> declare
  2     name varchar(10);
  3     no number(10);
  4     dnumber number(10);
  5     begin
  6         select empno,ename,deptno into no,name,dnumber from emp
  7         where sal>2000 and job like '%MAN%' and deptno = 10;
  8          dbms_output.put_line('Employee number is :'|| no);
  9          dbms_output.put_line('Employee name is :'|| name);
 10         dbms_output.put_line('Employee dno is :'|| dnumber);
 11      end;
 12     /

 3) Construct a PL/SQL block to obtain the employee number, name, and hire date for the employee with EMPNO 7782.
SQL> declare
  2      name varchar(10);
  3      Hdate date;
  4      no number(10);
  5  begin
  6      select empno,ename,hiredate into no,name,Hdate from emp
  7      where empno = 7782;
  8      dbms_output.put_line('Employee number is :'|| no);
  9      dbms_output.put_line('Employee name is :'|| name);
 10      dbms_output.put_line('Employee hiredate is :'|| Hdate);
 11   end;
 12   /

 4) Write a PL/SQL block to identify the employee number, name, and commission of the employee receiving the highest commission.

SQL> declare
  2      no number(10);
  3       name varchar(10);
  4      commission number(10);
  5  begin
  6      select empno,ename,comm into no,name,commission from emp
  7  where comm = (select max(comm) from emp);
  8
  9      dbms_output.put_line('Employee number is :'|| no);
 10      dbms_output.put_line('Employee name is :'|| name);
 11      dbms_output.put_line('Employee commission is :'|| commission);
 12   end;
 13   /

 5) Create a PL/SQL block to retrieve the employee number, name, and job title for the employee whose job is 'SALESMAN' and whose name ends with the letter 'D'.

SQL> declare
  2       name varchar(10);
  3         no number(10);
  4         job varchar(10);
  5        begin
  6             select empno,ename,job into no,name,job from emp
  7             where job like 'SALESMAN' and ename like '%D';
  8              dbms_output.put_line('Employee number is :'|| no);
  9              dbms_output.put_line('Employee name is :'|| name);
 10            dbms_output.put_line('Employee job is :'|| job);
 11         end;
 12        /

 6) Develop a PL/SQL block to fetch the employee number, name, and salary of the employee earning the second-highest salary.

SQL> declare
  2          no number(10);
  3           name varchar(10);
  4          salary number(10);
  5      begin
  6         select empno,ename,sal into no,name,salary from emp
  7      where sal = (select max(sal) from emp
  8                   where sal < (select max(sal) from emp)
  9                   );
 10
 11         dbms_output.put_line('Employee number is :'|| no);
 12         dbms_output.put_line('Employee name is :'|| name);
 13         dbms_output.put_line('Employee salary is :'|| salary);
 14      end;
 15      /

 7) Write a PL/SQL block to retrieve the employee number, name, and department number for the employee with the earliest hire date in the organization.

SQL> declare
  2         name varchar(10);
  3        no number(10);
  4        dnumber number(10);
  5         begin
  6             select empno,ename,deptno into no,name,dnumber from emp
  7             where hiredate = (select min(hiredate) from emp);
  8              dbms_output.put_line('Employee number is :'|| no);
  9             dbms_output.put_line('Employee name is :'|| name);
 10          dbms_output.put_line('Employee dno is :'|| dnumber);
 11        end;
 12        /

 8) Construct a PL/SQL block to obtain the employee number, name, and salary of the highest-paid employee in department 30.

SQL> declare
  2          no number(10);
  3          name varchar(10);
  4          salary number(10);
  5      begin
  6          select empno,ename,sal into no,name,salary from emp
  7      where sal = (select max(sal) from emp where deptno = 30);
  8
  9       dbms_output.put_line('Employee number is :'|| no);
 10         dbms_output.put_line('Employee name is :'|| name);
 11         dbms_output.put_line('Employee salary is :'|| salary);
 12      end;
 13      /

 9) Write a PL/SQL block to fetch the employee number, name, and manager ID for the employee with EMPNO 7566.
SQL> declare
  2  no number(10);
  3  name varchar(10);
  4  mgrId number(10);
  5  begin
  6  select empno,ename,mgr into no,name,mgrId from emp where empno = 7566;
  7       dbms_output.put_line('Employee number is :'|| no);
  8            dbms_output.put_line('Employee name is :'|| name);
  9            dbms_output.put_line('Employee mgrId is :'|| mgrId);
 10  end;
 11  /

 10) Create a PL/SQL block to retrieve the employee number, name, and job title for the employee designated as 'MANAGER' and hired in the month of April.

SQL> declare
  2     no number(10);
  3     name varchar(10);
  4     job varchar(10);
  5      begin
  6    	     select empno,ename,mgr into no,name,job from emp where job = 'MANAGER' and hiredate like '%APR%';
  7          dbms_output.put_line('Employee number is :'|| no);
  8          dbms_output.put_line('Employee name is :'|| name);
  9          dbms_output.put_line('Employee job is :'|| job);
 10     end;
 11     /

 11) Write a PL/SQL block to fetch the employee number, name, and salary of the employee named 'KING'.
SQL> declare
  2  no number(10);
  3  name varchar(10);
  4  sal number(10);
  5  begin
  6  select empno,ename,sal into no,name,sal from emp where ename = 'KING';
  7  dbms_output.put_line('Employee number is :'|| no);
  8             dbms_output.put_line('Employee name is :'|| name);
  9             dbms_output.put_line('Employee sal is :'|| sal);
 10
 11  end;
 12  /

 12) Develop a PL/SQL block to retrieve the employee number, name, and job title for the employee who was most recently hired.

 SQL> declare
  2             name varchar(10);
  3            no number(10);
  4            job varchar(10);
  5             begin
  6                select empno,ename,job into no,name,job from emp
  7                 where hiredate = (select max(hiredate) from emp);
  8                  dbms_output.put_line('Employee number is :'|| no);
  9                 dbms_output.put_line('Employee name is :'|| name);
 10             dbms_output.put_line('Employee job is :'|| job);
 11           end;
 12          /

 13) Construct a PL/SQL block to obtain the employee number, name, and department number for the employee earning a salary of exactly 800.
SQL> DECLARE
  2      name     VARCHAR2(10);
  3      no       NUMBER(10);
  4      deptnum  NUMBER(10);
  5  BEGIN
  6      SELECT empno, ename, deptno
  7      INTO no, name, deptnum
  8      FROM emp
  9      WHERE sal = 800;
 10
 11      DBMS_OUTPUT.PUT_LINE('Employee number is : ' || no);
 12      DBMS_OUTPUT.PUT_LINE('Employee name is   : ' || name);
 13      DBMS_OUTPUT.PUT_LINE('Employee deptnum is: ' || deptnum);
 14
 15  EXCEPTION
 16      WHEN NO_DATA_FOUND THEN
 17          DBMS_OUTPUT.PUT_LINE('No employee found with salary = 800.');
 18      WHEN TOO_MANY_ROWS THEN
 19          DBMS_OUTPUT.PUT_LINE('Multiple employees found with salary = 800. Please use a cursor or add more filters.');
 20  END;
 21  /


 14) Write a PL/SQL block to fetch the employee number, name, and commission for the employee receiving a commission of 1400.
DECLARE
    name     VARCHAR2(10);
    no       NUMBER(10);
    deptnum  NUMBER(10);
BEGIN
    SELECT empno, ename, deptno
    INTO no, name, deptnum
    FROM emp
    WHERE sal = 800;

    DBMS_OUTPUT.PUT_LINE('Employee number is : ' || no);
    DBMS_OUTPUT.PUT_LINE('Employee name is   : ' || name);
    DBMS_OUTPUT.PUT_LINE('Employee deptnum is: ' || deptnum);

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee found with salary = 800.');
    WHEN TOO_MANY_ROWS THEN
        DBMS_OUTPUT.PUT_LINE('Multiple employees found with salary = 800.');
END;
/


 15) Create a PL/SQL block to retrieve the employee number, name, and job title for the employee who does not report to any manager (i.e., MGR is NULL).

DECLARE
    v_empno  emp.empno%TYPE;
    v_ename  emp.ename%TYPE;
    v_job    emp.job%TYPE;
BEGIN
    SELECT empno, ename, job
    INTO v_empno, v_ename, v_job
    FROM emp
    WHERE mgr IS NULL;

    DBMS_OUTPUT.PUT_LINE('Employee Number : ' || v_empno);
    DBMS_OUTPUT.PUT_LINE('Employee Name   : ' || v_ename);
    DBMS_OUTPUT.PUT_LINE('Job Title       : ' || v_job);
EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee found with MGR = NULL.');
    WHEN TOO_MANY_ROWS THEN
        DBMS_OUTPUT.PUT_LINE('Multiple employees found with MGR = NULL. Use a cursor.');
END;
/

-------------------------------------------------------------------------------------------------------------------

