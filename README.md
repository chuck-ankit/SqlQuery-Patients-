# Task 2: Querying Patients with Type I Diabetes

## Question
You are provided with a table named `Patients`, which contains information about the patients in a hospital. The table has the following structure:

| Column Name   | Type    |
|---------------|---------|
| patient_id    | int     |
| patient_name  | varchar |
| conditions    | varchar |

- `patient_id` is the primary key (column with unique values) for this table.
- The `conditions` column contains 0 or more codes separated by spaces.

Your task is to find the `patient_id`, `patient_name`, and `conditions` of the patients who have **Type I Diabetes**. Type I Diabetes is identified by codes that always start with the prefix `DIAB1`.

### Example Input
**Patients table:**

| patient_id | patient_name | conditions   |
|------------|--------------|--------------|
| 1          | Daniel       | YFEV COUGH   |
| 2          | Alice        |              |
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 |
| 5          | Alain        | DIAB201      |

### Example Output
| patient_id | patient_name | conditions   |
|------------|--------------|--------------|
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 |

### Explanation
- Patients Bob and George have conditions that include a code starting with the prefix `DIAB1` (e.g., `DIAB100`). Hence, they are included in the output.

---

## Solution
To solve this task, we will write a SQL query that filters the rows based on the presence of codes starting with `DIAB1` in the `conditions` column. Here is the SQL query:

```sql
SELECT
    patient_id,
    patient_name,
    conditions
FROM
    Patients
WHERE
    conditions LIKE '%DIAB1%';
```

### Explanation of the Query
1. **SELECT Clause**:
   - Retrieves the `patient_id`, `patient_name`, and `conditions` columns from the `Patients` table.

2. **WHERE Clause**:
   - Filters the rows where the `conditions` column contains the substring `DIAB1`.
   - The `LIKE '%DIAB1%'` ensures that any occurrence of `DIAB1`, regardless of its position in the string, is matched.

### Execution on Example Data
Given the `Patients` table:

| patient_id | patient_name | conditions   |
|------------|--------------|--------------|
| 1          | Daniel       | YFEV COUGH   |
| 2          | Alice        |              |
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 |
| 5          | Alain        | DIAB201      |

The query will produce the following result:

| patient_id | patient_name | conditions   |
|------------|--------------|--------------|
| 3          | Bob          | DIAB100 MYOP |
| 4          | George       | ACNE DIAB100 |

### Notes
- If the `conditions` column format changes (e.g., codes separated by commas instead of spaces), the query may require adjustments.
- For large datasets, consider optimizing the query with indexes or text-search mechanisms.

---

This solution effectively identifies patients with Type I Diabetes based on the provided table and requirements.

