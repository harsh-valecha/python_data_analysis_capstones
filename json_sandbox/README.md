# JSON Sandbox Practice

This folder contains a dummy JSON dataset for practicing Python JSON operations such as reading, filtering, transforming, and writing JSON files.

## Files

- `practice_data.json` - A more complex sample dataset representing employees, projects, tasks, and analytics.

## Suggested Practice Questions

1. Load the JSON file and print the company name.
2. Count how many employees are present in the dataset.
3. Find all employees whose `active` field is `true`.
4. List the names of employees working in the `Data Science` department.
5. Find the employee with the highest `performance.rating`.
6. Print all project names for each employee.
7. Count how many tasks are marked as `completed: true` across all employees.
8. Extract the `skills` list from each employee and flatten them into one combined list.
9. Find employees who have `remote_ok` set to `true`.
10. Identify which employee has the most projects.
11. Calculate the average performance rating for all employees.
12. Update one employee's city and save the JSON file back to disk.
13. Add a new employee to the `employees` array and write the updated data.
14. Filter employees by department and print only their names.
15. Find all employees who have the skill `Python`.

## Example Python Snippets

### Read JSON

```python
import json

with open('json_sandbox/practice_data.json', 'r') as file:
    data = json.load(file)

print(data['company']['name'])
```

### Count employees

```python
print(len(data['employees']))
```

### Filter active employees

```python
active_employees = [emp for emp in data['employees'] if emp['active']]
print([emp['name'] for emp in active_employees])
```

### Modify and save JSON

```python
for emp in data['employees']:
    if emp['id'] == 1:
        emp['city'] = 'Boston'

with open('json_sandbox/practice_data.json', 'w') as file:
    json.dump(data, file, indent=2)
```

## Practice Ideas

- Read JSON from file and convert it into Python dictionaries/lists.
- Filter data with list comprehensions.
- Use nested loops for projects and tasks.
- Write updated data back into the JSON file.
- Explore how JSON maps to Python data structures.
