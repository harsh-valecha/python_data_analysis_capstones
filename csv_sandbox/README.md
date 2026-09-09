# CSV Practice Problems for Python

This folder contains sample CSV files for practicing reading, writing, and basic data analysis with Python.

## Files

- `sample.csv` — a simple CSV file for beginner practice
- `practice_data.csv` — a richer dataset with more columns and rows for intermediate practice

## Practice Problems

1. Read the CSV file and print the total number of rows.
2. Read the CSV file and print the column names.
3. Read the CSV file and print only the first 5 rows.
4. Read the CSV file and calculate the average age.
5. Read the CSV file and count how many people are from each city.
6. Read the CSV file and find the oldest person.
7. Read the CSV file and find the youngest person.
8. Read the CSV file and calculate the average salary.
9. Read the CSV file and count how many active users there are.
10. Read the CSV file and count how many inactive users there are.
11. Read the CSV file and find the highest-paid employee.
12. Read the CSV file and find the lowest-paid employee.
13. Read the CSV file and filter rows where `age > 30`.
14. Read the CSV file and filter rows where `country == "USA"`.
15. Read the CSV file and sort rows by `age` in descending order.
16. Read the CSV file and sort rows by `salary` in ascending order.
17. Read the CSV file and write a new CSV containing only `id, first_name, last_name, salary`.
18. Read the CSV file and write a new CSV containing only active users.
19. Read the CSV file and add a new column called `salary_group` based on salary ranges.
20. Read the CSV file and create a summary report showing total employees, average age, and average salary.

## Suggested Workflow

1. Start with the simple `sample.csv` file.
2. Move to `practice_data.csv` for more realistic data analysis.
3. Try solving the questions using Python's built-in `csv` module.
4. Then try the same tasks using `pandas` for faster analysis.

## Extra Challenges

- Handle missing values gracefully.
- Validate that the CSV file has the expected columns.
- Write a script that reads the CSV, cleans invalid rows, and saves the cleaned version.
- Compare results between the `csv` module and `pandas`.

## Quick Tips

- Use `csv.DictReader` for row-by-row access.
- Use `csv.writer` to write new CSV files.
- Use `statistics.mean()` or `pandas.Series.mean()` for averages.
- Use `sorted()` or DataFrame methods for sorting.
