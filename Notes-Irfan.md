ALTER TABLE MODIFY :- It is used to modify the existing coloumn in a table . Multiple coloumns can be modified at one
 
 SYNTAX :- ALTER TABLE TABLENAME
    MODIFY COLOUMN_NAME COLOUMN_TYPE

 SYNTAX(SQL SERVER)-> ALTER TABLE TABLE_NAME
              ALTER COLOUMN_NAME COLOUMN_TYPE

DML COMMANDS: The sql comands that deals with manipulation of data present in the database belongs to DML or data manipulation language and this includes most of the sql statments.

List of DML commands:

1. SELECT -> It is used to retrieve data from the database.  

 SYNTAX: SELECT COL1,COL2,COL3
  FROM TABLE
  WHERE CONDITION

2. INSERT -> It is used to insert data into a table.
3. UPDATE -> It is used to update the existing data into a table.
4. DELETE -> It is used to delete records from database table.

QUESTION - You have name,rollno,address,fathername,marks DISPLAY THE QUERY

1. display the details of student whose name is ALOK  
  SELECT * FROM STUDENT WHERE NAME = 'ALOK'.

2. display the name of student and roll number whose name is AMIT and father name is RAGVENDRA.
  SELECT NAME,ROLLNO FROM STUDENT WHERE NAME = 'AMIT' AND FNAME = 'RAGVENDRA'

3. dispaly the name and rollnumber of students whose marks are greter then 50.
  SELECT NAME,ROLLNO FROM STUDENT WHERE MARKS > 50

4. dispaly the name and address of the student whose roll number is 100040011161.
  SELECT NAME,ADDRESS FROM STUDENT WHERE ROLLNO = '100040011161'

5. dispaly the names and fathers name of the student and roll no whose marks is greater then 50 and his name is AMIT.
  SELECT NAME,FNAME,ROLLNO FROM STUDENT WHERE MARKS > 50 AND NAME = 'AMIT'

``````````````````````````````````````````````````````   INSERT     ````````````````````````````````````````````````````````````````

1.INSERT INTO :- first method is to specify only the value of data to be inserted without the coloumn names
     SYNTAX ->  INSERT INTO  TABLE_NAME VALUES(VALUE1,VALUE2,VALUE3,.....);

   example ->INSERT INTO STUDENT VALUES('AMIT',100334,

2. COLOUMNS NAMES AND VALUE BOTH :- In the  second methos we will specify both the coloumns which we want to fill, and their
         corresponding values as shown below.

   SYNTAX -> INSERT INTO TABLE_NAME(COL1,COL2,COL3,.......) VALUES (VALUE1,VALUE2,VALU3,........) 
    
   EXAMPLE -> INSERT INTO STUDENT(ROLL_NUMBER,NAME,MARKS,......) VALUES (50010012164,'PRATEEK',60)

3. USING SELECT INSERT INTO

 We can use select stametnt with INSERT INTO statemnt to copy rows from one table and INSERT them into another table , the use of this statment is similar to  that of INSERT INTO statemnet , the diffrence is the the SELECT statemnt is used here to SELECT data from a dffrent table .
the diffrent ways to use INSERT INTO SELECT stament is :

1. INSERTING ALL COLOUMNS OF A TABLE .
  SYNTAX-> INSERT INTO first_table SELECT * FROM second_table

2.INSERTING SPECIFIC COLOUMNS OF A TABLE:- WE can copy only those coloumns of a tbale which we want to insert intoa diffrent table

  INSERT INTO first_table (names_of_coloumns) SELECT names_of_coloumn FROM second_table

3.COPYING SPECIFING ROWS OF A TABLE:- we cn copy specific rows from a table to insert into another table by using WHERE   clause with the SELECT statment.

   INSERT INTO table1 SELECT * FROM table2 WHERE condition

4.TO INSERT MULTPLE ROWS IN A TABLE USING SINGLE SQL SATMENT :-

  INSERT INTO table_name(col1,col2,col3,....)
  VALUES(val1,val2,val3,..........) , 
  (val1,val2,val3,..........) , 
  (val1,val2,val3,.......) , 
  (val1,val2,val3,.......)
  
         ...........); 

---------------------------------------- DISTINCT ----------------------

SELECT DISTINCT CAOL1,COL2,.............
FROM TABLE_NAME

DISTINCT command will return the distinct values from the given table .

------------------------------------ RELATIONAL OPERATORS ---------------------------------
EQUAL , > , < , >= , != , NOT EQUAL , BETWEEN (between a certaion value) , LIKE

QUESTIONS

  Display the details of students whose name starts with letter 'A'
  SELECT NAME FROM STUDENT WHERE NAME LIKE 'A%'

  Display the name and roll no of student having second charater in their name as 'U'
  SELECT NAME,ROLLNO FROM STUDENT WHERE NAME LIKE '_U%'

  Display the details of student whose name ends with character 'Q'
  SELECT * FROM STUDENT WHERE NAME LIKE '%Q'

  Display the details of student having exactly five charaters in their name and the third char is 'O'
  SELECT * FROM STUDENT WHERE NAME LIKE '____O'
  
   POINT TO BE NOTED -> (____0 means o is at 5 postion form starting {4 times underscore}).

  Dispaly the name and rno having DOB ending with 01
  SELECT NAME,ROLLNO FROM STUDENT WHERE DOB LIKE '01%'

  dispaly the details of student whose DOB starts with 11
  SELECT * FROM STUDENT WHERE DOB LIKE '11%'

THREE OPERATORS WE ALSO USE WITH WHERE
AND , OR -> the AND OR operators are  used to filter records based on more then one conditions.

NOT ->  SELECT COL1,COL2 FROM table_name WHERE NOT condition

QUESTION

 DISPLAY the details of student whose marks is greater then 60 and his name starts with letter 'D'
  SELECT * FROM STUDENT WHERE MARKS > 60 AND NAME LIKE 'D%'

 display the details of student whose name is NOT 'AMIT'
  SELECT * FROM STUDENT WHERE  NOT NAME 'AMIT'

 dispaly the details of student whose name is 'ATUL' and marks are either 60 or 70
  SELECT * FROM STUDENT WHERE NAME = 'ATUL' AND MARKS  IN(60,70)
  SELECT * FROM STUDENT WHERE NAME = 'ATUL' AND (MARKS = 60 OR MARKS = 70)
 
 dispaly the details of student whose marks greter then 60 but not exactly equal to 80 or 90
  SELECT * FROM STUDENT WHERE MARKS > 60 AND MARKS NOT IN(80,90)
  SELECT * FROM STUDENT WHERE MARKS > 60 AND (MARKS != 80 OR MARKS != 90)

------------------------------------- ORDER BY--------------------------------------

The order by keyword is used to sort the result set in ascending or descending order. the ORDER BY sorts the record in ascending order by default , to sort the records in descending order used the DESC keyword.

 SELECT COL1,COL2............ FROM table_name ORDER BY  COL1,COL2......... ASC/DESC

 dispaly the details of student according to their marks in descending order
  SELECT * FROM STUDENT ORDER BY MARKS DESC

 display the name and roll no of student in accordiing to their name is ascending order
  SELECT NAME,ROLLNO FROM STUDENT ORDER BY NAME

ORDER BY IN SEVERAL QUERY

the sql staments selects all student marks if some rows has rhe same marks then it orders them by name;

QUESTION
` 
display the name and roll no of the student who have not entered their fathes name.
SELECT NAME,ROLLNO FROM STUDENT WHERE FNAME IS NULL

display the name and rollno of the student wose name starts with letter 'A' and thier marks are not filled in the database
SELECT NAME,ROLLNO FROM STUDENT WHERE NAME LIKE 'A%' AND MARKS IS NULL

-------------------------- WILDCARD IN LIKE CLAUSE ----------------------
the LIKE keywords selects the ros containing feilds that match specified portions of character string .

LIKE is used with char ,varchar,text, datetime and small datetime data a wild card allows the user to match feilds that contains certain letters.

```WILDCARDS````

% : any string 0 or more characters.
_(underscore) :  Any single characters
[] : any single character within the specified range.
[^ ] : any single character not within the specified range.

QUESTION

- display the marks and roll no of student whose name start with MAC

```sql
SELECT MARKS,ROLLNO FROM STUDENT WHERE NAME LIKE 'MAC%'
```

- display the name and rollno of the student whose name ends with 'KUMAR'.

```sql
SELECT MARKS,ROLLNO FROM STUDENT WHERE NAME LIKE '%KUMAR'
```

- dispaly the name roll no and marks o student that have 'em' as a subscript in his name

```sql
SELECT MARKS, ROLLNO FROM STUDENT WHERE NAME LIKE '%em%';
```

- display the name and rollno of student whose name starts with a,b,c, and marks > 60

```sql
SELECT MARKS,ROLLNO FROM STUDENT WHERE NAME LIKE '[a-c]r%' AND MARKS>60;
```

#### Using group by clause - [abc]%

- With group by clause is use to create row per each group an produces summary values for the selected columns

```SQL
SELECT COLUMN1, COLUMN2 ... FROM TABLE_NAME GROUP BY COLUMN1
```

- display the city wise maximum marks from the student avg marks.

- You have to display he authors name country wise but country should not be Russia an china an pakistan.

#### upate statement

- change ata in existring rows either b aing new ata or madifying existing data

UPDATE table_name =set VALUE ;

USING UPDATE WHERE SET COLUMN WHERE CONDITION;

- Change the To instee of Raghvenra
- change the marks of the stuent to 60.1 where marks is 60
- increase the marks of the student by 10% where city is kanpur
