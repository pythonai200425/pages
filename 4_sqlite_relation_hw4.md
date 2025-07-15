## דף עבודה לאימון SQL - סוגי קשרים (1:1, 1\:N, M\:N)

### מבנה:

התרגיל כולל שלוש קבוצות טבלאות המדגימות שלושה סוגים של קשרים במסדי נתונים:

* קשר אחד-לאחד (1:1)
* קשר אחד-לרבים (1\:N)
* קשר רבים-לרבים (M\:N)

---

### 🔹 קשר 1:1 - משתמשים וסיסמאות (users + passwords)

#### יצירת טבלאות:

```sql
CREATE TABLE users (
    user_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL
);

CREATE TABLE passwords (
    user_id INTEGER UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    FOREIGN KEY(user_id) REFERENCES users(user_id)
);
```

#### הוספת נתונים:

```sql
INSERT INTO users (user_id, name) VALUES
(1, 'Lior'), (2, 'Tamar'), (3, 'Erez'), (4, 'Dana'),
(5, 'Amit'), (6, 'Yael'), (7, 'Noam'), (8, 'Hila'),
(9, 'Aviad'), (10, 'Shani');

INSERT INTO passwords (user_id, password_hash) VALUES
(1, 'abc123'), (2, 'pass456'), (3, 'hello789'), (4, 'secure321'),
(5, 'qwerty12'), (6, 'secret99');
```

#### משימות:

* הצג את כל המשתמשים עם הסיסמה שלהם (INNER JOIN)
* הצג את כל המשתמשים, גם כאלה שאין להם סיסמה (LEFT JOIN)
* הצג את המשתמשים שאין להם סיסמה כלל

---

### 🔹 קשר 1\:N - עובדים ומחלקות (employees + departments)

#### יצירת טבלאות:

```sql
CREATE TABLE departments (
    department_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL
);

CREATE TABLE employees (
    employee_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    department_id INTEGER,
    FOREIGN KEY(department_id) REFERENCES departments(department_id)
);
```

#### הוספת נתונים:

```sql
INSERT INTO departments (department_id, name) VALUES
(1, 'Finance'), (2, 'IT'), (3, 'HR'), (4, 'Marketing');

INSERT INTO employees (employee_id, name, department_id) VALUES
(1, 'Shira', 1), (2, 'Doron', 2), (3, 'Tal', 2), (4, 'Adi', 3),
(5, 'Omer', NULL), (6, 'Yoni', 1), (7, 'Michal', NULL),
(8, 'Liad', 4), (9, 'Noga', 2), (10, 'Rami', 1);
```

#### משימות:

* הצג את כל העובדים עם שם המחלקה שלהם
* הצג את כל המחלקות והעובדים שלהן
* הצג את כל העובדים כולל כאלה שלא שויכו למחלקה
* הצג מחלקות שאין בהן אף עובד

---

### 🔹 קשר M\:N - אזרחים וחברות כבלים (citizens + cable\_tv + subscriptions)

#### יצירת טבלאות:

```sql
CREATE TABLE citizens (
    citizen_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL
);

CREATE TABLE cable_tv (
    company_id INTEGER PRIMARY KEY,
    name TEXT NOT NULL
);

CREATE TABLE subscriptions (
    citizen_id INTEGER,
    company_id INTEGER,
    PRIMARY KEY (citizen_id, company_id),
    FOREIGN KEY(citizen_id) REFERENCES citizens(citizen_id),
    FOREIGN KEY(company_id) REFERENCES cable_tv(company_id)
);
```

#### הוספת נתונים:

```sql
INSERT INTO citizens (citizen_id, name) VALUES
(1, 'Rina'), (2, 'Avi'), (3, 'Lea'), (4, 'Moshe'),
(5, 'Gali'), (6, 'Bar'), (7, 'Itai'), (8, 'Sivan'),
(9, 'Elior'), (10, 'Hodaya');

INSERT INTO cable_tv (company_id, name) VALUES
(1, 'HOT'), (2, 'YES'), (3, 'Partner TV');

INSERT INTO subscriptions (citizen_id, company_id) VALUES
(1, 1), (1, 2),
(2, 2), (2, 3),
(3, 1), (4, 1),
(5, 3), (6, 3), (6, 1),
(7, 2);
```

#### משימות:

* הצג את כל המנויים עם שם האזרח ושם החברה
* הצג את כל האזרחים וכמה חברות הם מנויים אליהן
* הצג את כל חברות הכבלים וכמה מנויים יש להן
* הצג אזרחים שלא מנויים לאף חברה
* הצג חברות שאין להן אף מנוי

## 📤 הגשה

יש לשלוח את הפתרון עם כל שלבי התרגול והמימושים למייל:
📧 [pythonai200425+sqlitehw2@gmail.com](mailto:pythonai200425+sqlitehw4@gmail.com)
