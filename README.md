# International Students Mental Health Analysis (SQL)

## 📝 Overview

This project explores how studying abroad influences emotional well-being. Using SQL queries inside a PostgreSQL database, I analyze the relationship between **length of stay** and three key mental-health diagnostic tests:

* **PHQ-9 (todep)** – depression severity
* **SCS (tosc)** – self-compassion score
* **ASISS (toas)** – acculturative stress level

The analysis focuses **only on international students**, following the original project guidelines.

---

## 📚 Dataset Structure

Your final combined `students` table contains the following important fields:

| Column      | Description                                               |
| ----------- | --------------------------------------------------------- |
| `inter_dom` | Student type: `Inter` (international) or `Dom` (domestic) |
| `stay`      | Length of stay in Japan                                   |
| `todep`     | PHQ-9 depression score                                    |
| `tosc`      | SCS self-compassion score                                 |
| `toas`      | ASISS acculturative stress score                          |

---

## 🧪 SQL Analysis Steps

### 1. Filter for international students

Ensures the analysis focuses only on `Inter` students:

```sql
WHERE inter_dom = 'Inter'
```

### 2. Group by length of stay

```sql
GROUP BY stay
```

### 3. Count students per stay category

```sql
COUNT(*) AS count_int
```

### 4. Calculate average diagnostic scores

Rounded to two decimals using `ROUND()`.

### 5. Sort results from longest stay to shortest

```sql
ORDER BY stay DESC
```

---

## 🧩 Final SQL Query

```sql
SELECT
    stay,
    COUNT(*) AS count_int,
    ROUND(AVG(todep), 2) AS average_phq,
    ROUND(AVG(tosc), 2) AS average_scs,
    ROUND(AVG(toas), 2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC;
```

---

## 📈 Results Summary

Running the query produces a **9-row output**, each representing one length-of-stay category for international students.

For each stay group, you can analyze:

* How many international students fall into each category
* Their average PHQ-9 score (depression)
* Their average SCS score (self-compassion)
* Their average ASISS score (acculturative stress)

These metrics help observe how adaptation time may influence psychological well-being.

---
