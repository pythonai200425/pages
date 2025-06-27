# 📘 לימוד SQLite עם טבלת COMPANY

<div dir="rtl" style="text-align: right">


---

## יצירת טבלה – CREATE TABLE

```sql
-- יצירת טבלה עם שדות לעובדים: מזהה, שם, גיל, כתובת ומשכורת
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

```sql
-- הוספת עובדים שונים עם גיל, כתובת ומשכורת
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

## SELECT בסיסי

```sql
-- מציג את כל השורות והעמודות מהטבלה
SELECT * FROM COMPANY;
```

```
1 | Paul  | 32 | California | 20000.00
2 | Allen | 25 | Texas      | 15000.00
...
```

```sql
-- מחזיר את הגיל הכי גבוה בטבלה
SELECT MAX(AGE) FROM COMPANY;
-- פלט: 32
```

```sql
-- מחזיר את הגיל הכי נמוך בטבלה
SELECT MIN(AGE) FROM COMPANY;
-- פלט: 22
```

```sql
-- מחשב את ממוצע הגילאים
SELECT AVG(AGE) FROM COMPANY;
-- פלט: 25.43
```

---

## ביטויים מתמטיים ופונקציות

```sql
SELECT 1;                    -- פלט: 1
SELECT 5 + 3;                -- פלט: 8
SELECT 1.0 / 100;            -- פלט: 0.01
SELECT pow(2, 5);            -- פלט: 32
SELECT sqrt(49);             -- פלט: 7
SELECT ABS(-15);             -- פלט: 15
SELECT ROUND(3.14159, 2);    -- פלט: 3.14
```

---

## תאריכים ושעה

```sql
SELECT CURRENT_DATE;                      -- פלט: 2025-06-27
SELECT CURRENT_TIME;                      -- פלט: 14:52:03
SELECT CURRENT_TIMESTAMP;                 -- פלט: 2025-06-27 14:52:03
SELECT datetime('now', 'localtime');      -- פלט: 2025-06-27 17:52:03
SELECT strftime('%Y', 'now');             -- פלט: 2025
```

---

## סינון עם WHERE, IN, LIKE, BETWEEN

```sql
-- כל העובדים שהשכר שלהם גבוה מ־4500
SELECT * FROM COMPANY WHERE SALARY > 4500;

-- כל העובדים שגילם גדול מ־25
SELECT * FROM COMPANY WHERE AGE > 25;

-- כל העובדים שהכתובת שלהם היא Texas בדיוק
SELECT * FROM COMPANY WHERE ADDRESS = 'Texas';

-- כל העובדים ששמם הוא Kim
SELECT * FROM COMPANY WHERE NAME = 'Kim';

-- עובדים שגרים בטקסס ומרוויחים יותר מ־50,000
SELECT * FROM COMPANY WHERE ADDRESS = 'Texas' AND SALARY > 50000;

-- עובדים שכתובתם או Texas או Norway
SELECT * FROM COMPANY WHERE ADDRESS IN ('Texas', 'Norway');

-- עובדים ששמם כולל את האות a (בכל מקום בשם)
SELECT * FROM COMPANY WHERE NAME LIKE '%a%';

-- עובדים בגיל בין 25 ל־27 כולל
SELECT * FROM COMPANY WHERE AGE BETWEEN 25 AND 27;
```

---

## הגבלת כמות שורות – LIMIT ו־OFFSET

```sql
-- מציג שלוש הרשומות הראשונות בטבלה
SELECT * FROM COMPANY LIMIT 3;

-- מדלג על שתי הרשומות הראשונות ומחזיר את שלוש הבאות
SELECT * FROM COMPANY LIMIT 3 OFFSET 2;
```

---

## מיון שורות עם ORDER BY

```sql
-- ממיין את העובדים לפי גיל בסדר עולה (מהקטן לגדול)
SELECT * FROM COMPANY ORDER BY AGE ASC;

-- ממיין את העובדים לפי שכר מהגבוה לנמוך
SELECT * FROM COMPANY ORDER BY SALARY DESC;

-- מציג את שמות שני העובדים שמרוויחים הכי הרבה
SELECT NAME FROM COMPANY ORDER BY SALARY DESC LIMIT 2;

-- מדלג על שניים ומחזיר את שמות העובדים הבאים ברשימה לפי שכר
SELECT NAME FROM COMPANY ORDER BY SALARY DESC LIMIT 2 OFFSET 2;
```

</div>
