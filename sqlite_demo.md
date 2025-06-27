# 📘 לימוד SQL עם טבלת COMPANY

<div dir="rtl" style="text-align: right">

כל הקוד במסמך זה כתוב ב־SQL בלבד. הקוד אינו מיועד להרצה מתוך המחברת אלא ללימוד, הסבר והצגה נוחה.

---

## יצירת טבלה – CREATE TABLE

הטבלה שניצור נקראת `COMPANY` וכוללת מזהה, שם, גיל, כתובת ומשכורת.

```sql
CREATE TABLE COMPANY(
  ID INT PRIMARY KEY NOT NULL,
  NAME TEXT NOT NULL,
  AGE INT NOT NULL,
  ADDRESS CHAR(50),
  SALARY REAL
);
```

---

## הכנסת נתונים – INSERT INTO

הוספת עובדים שונים עם פרטי גיל, כתובת ומשכורת.

```sql
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (1, 'Paul', 32, 'California', 20000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (2, 'Allen', 25, 'Texas', 15000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (3, 'Teddy', 23, 'Norway', 20000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (5, 'David', 27, 'Texas', 85000.00 );

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
VALUES (6, 'Kim', 22, 'South-Hall', 45000.00 );

INSERT INTO COMPANY VALUES (7, 'James', 24, 'Houston', 10000.00 );
```

---

## שאילתות בסיסיות – SELECT

```sql
SELECT * FROM COMPANY;

SELECT MAX(AGE) FROM COMPANY;

SELECT MIN(AGE) FROM COMPANY;

SELECT AVG(AGE) FROM COMPANY;
```

---

## ביטויים ומתמטיקה ב־SQL

```sql
SELECT 1;

SELECT 5 + 3;

SELECT 1.0 / 100;

SELECT pow(2, 5);

SELECT sqrt(49);

SELECT ABS(-15);

SELECT ROUND(3.14159, 2);
```

---

## תאריכים ושעה נוכחית

```sql
SELECT CURRENT_DATE;

SELECT CURRENT_TIME;

SELECT CURRENT_TIMESTAMP;

SELECT datetime('now', 'localtime');

SELECT strftime('%Y', 'now');
```

---

## סינון נתונים – WHERE, IN, LIKE, BETWEEN

```sql
SELECT * FROM COMPANY WHERE SALARY > 4500;

SELECT * FROM COMPANY WHERE AGE > 25;

SELECT * FROM COMPANY WHERE ADDRESS = 'Texas';

SELECT * FROM COMPANY WHERE NAME = 'Kim';

SELECT * FROM COMPANY WHERE ADDRESS = 'Texas' AND SALARY > 50000;

SELECT * FROM COMPANY WHERE ADDRESS IN ('Texas', 'Norway');

SELECT * FROM COMPANY WHERE NAME LIKE '%a%';

SELECT * FROM COMPANY WHERE AGE BETWEEN 25 AND 27;
```

---

## הגבלת תוצאות – LIMIT ו־OFFSET

```sql
SELECT * FROM COMPANY LIMIT 3;

SELECT * FROM COMPANY LIMIT 3 OFFSET 2;
```

---

## מיון נתונים – ORDER BY

```sql
SELECT * FROM COMPANY ORDER BY AGE ASC;

SELECT * FROM COMPANY ORDER BY SALARY DESC;

SELECT NAME FROM COMPANY ORDER BY SALARY DESC LIMIT 2;

SELECT NAME FROM COMPANY ORDER BY SALARY DESC LIMIT 2 OFFSET 2;
```

---

## עדכון נתונים – UPDATE

```sql
UPDATE COMPANY 
SET ADDRESS = 'Texas', AGE = AGE + 1
WHERE ID = 7;
```

---

## מחיקת רשומות – DELETE

```sql
DELETE FROM COMPANY WHERE ID = 7;
```

</div>
