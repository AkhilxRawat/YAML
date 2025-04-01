# Python YAML Use Case

## Overview
This Python application demonstrates how to read, display, and filter student data from a YAML file. It allows users to view all students and filter them based on a specified minimum GPA.

## Prerequisites
Before running the application, ensure you have the required dependencies installed:

```sh
pip install pyyaml
```

## File Structure
```
project_directory/
│── app.py
│── students.yaml
│── README.md
```

## Step 1: Create the YAML File
Create a file named `students.yaml` with the following structure:

```yaml
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5
  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9
  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2
  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7
```

## Step 2: Create the Python Script
Create a file named `app.py` and add the following code:

```python
import yaml

def load_data(file_path):
    """Load data from a YAML file."""
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)
    return data

def display_students(students):
    """Display all student records."""
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """Filter and display students with a GPA above the specified minimum."""
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    print(f"\nStudents with GPA >= {min_gpa}:")
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    data = load_data('students.yaml')
    students = data['students']
    
    display_students(students)
    
    min_gpa = float(input("\nEnter minimum GPA to filter students: "))
    filter_students_by_gpa(students, min_gpa)

if __name__ == "__main__":
    main()
```

## Step 3: Run the Application
1. Ensure `students.yaml` and `app.py` are in the same directory.
2. Open a terminal and navigate to the project directory.
3. Run the script using:

```sh
python app.py
```

## Expected Output
When executed, the program will display all student records and prompt the user for a minimum GPA to filter students.

Example Output:
```
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: David, Age: 23, Major: Chemistry, GPA: 3.2
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7
```

## Additional Features
To enhance functionality, consider implementing the following features:
- **Sorting**: Allow users to sort students by GPA, age, or major.
- **Updating Data**: Enable users to modify student information and save updates back to the YAML file.
- **Saving Filtered Data**: Provide an option to save filtered student data to a new file for future reference.
- **User Interface**: Develop a simple GUI using Tkinter or a web interface using Flask for better usability.

## Conclusion
This application provides a simple yet effective way to read, display, and filter data from a YAML file using Python. Future enhancements could include sorting, updating student information, or saving modifications back to the YAML file, making it a more dynamic and useful tool.

