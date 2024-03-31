def calculate_grade(score):
    if score >= 90:
        return 'A'
    elif 80 <= score < 90:
        return 'B'
    elif 70 <= score < 80:
        return 'C'
    elif 60 <= score < 70:
        return 'D'
    else:
        return 'F'

def input_students():
    student_data = []
    for _ in range(5):
        student = {}
        student['Student_Number'] = input("Student_Number: ")
        student['Name'] = input("Name: ")
        student['English'] = int(input("English: "))
        student['C_programming'] = int(input("C_programming: "))
        student['Python'] = int(input("Python: "))
        student_data.append(student)
    return student_data

def calculate_total_average(students):
    for student in students:
        student['Total'] = student['English'] + student['C_programming'] + student['Python']
        student['Average'] = student['Total'] / 3

def calculate_rank(students):
    sorted_students = sorted(students, key=lambda x: x['Average'], reverse=True)
    for i, student in enumerate(sorted_students):
        student['Rank'] = i + 1

def print_results(students):
    print("\n=============================================================================================\n")
    print("Student_Number \t\tName \t\tEnglish    C_programming  Python   Total  Average    Grade   Rank")
    print("\n=============================================================================================\n")
    for student in students:
        print(f"{student['Student_Number']} \t {student['Name']} \t {student['English']} \t {student['C_programming']} \t {student['Python']} \t {student['Total']} \t {student['Average']} \t {calculate_grade(student['Average'])} \t {student['Rank']}")

def main():
    students = input_students()
    calculate_total_average(students)
    calculate_rank(students)
    print_results(students)

if __name__ == "__main__":
    main()
