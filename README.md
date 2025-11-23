# VTOP – VIT On TOP System

## Overview 
VTOP is a console-based, role-based system for students, faculty, parents, and alumni. Users can login and access information relevant to their role such as attendance, marks, timetable, assigned courses, and alumni events.

## Features
- Role-based login system (Student, Employee, Parent, Alumni)
- View attendance and marks (Student)
- View weekly timetable (Student)
- View courses assigned and students under supervision (Employee)
- View child’s name and attendance (Parent)
- View passout details and upcoming alumni events (Alumni)
- Logout functionality

## Technologies / Tools Used 
- Python 3.x
- Command-Line Interface (CLI)
- Data structures: Dictionaries
- Terminal/Console for input-output

##  Steps to Install & Run the Project
1. Make sure Python 3.x is installed on your system.
2. Download the project folder or clone the repository.
3. Open terminal (Mac) or command prompt (Windows) and navigate to the project folder.
  
##  Instructions for Testing

1. **Run the Program**
   - Open terminal (Mac) or command prompt (Windows)
   - Navigate to the project folder
   - Run the program:
   ```bash
   python3 main.py

```bash
python3 main.py

users = {
    "student": {"reg": "stu1", "pass": "1111", "name": "Aarav Singh"},
    "employee": {"reg": "emp1", "pass": "2222", "name": "Prof. S.Padhy"},
    "parent": {"reg": "par1", "pass": "3333", "name": "Mr. S.Singh"},
    "alumni": {"reg": "alm1", "pass": "4444", "name": "Atharav Pathak"}
}
attendance = {"CSE1021": 100, "PHY1003": 89, "MATHS1003": 93, "ENG1004": 95, "CHY1006": 75,}
marks = { "CSE1021": 48, "PHY1003": 46, "MATHS1003": 46, "ENG1004": 40, "CHY1006": 42,}

timetable = {
    "MON": "PHY1003 (08:30 - 10:00 AM) , MATH1003 (11:40 - 13:10 PM)",
    "TUE": "CSE1021 (10:05 - 11:35 AM) , ENG1004  (14:50 - 16:20 PM)",
    "WED": "PHY1003 (08:30 - 10:00 AM) , MATH1003 (11:40 - 13:10 PM) , CHY1006 (14:50- 16:20 PM)",
    "THU": "CSE1021 (10:05 - 11:35 AM)",
    "FRI": "PHY1003 (08:30 - 10:00 AM) , MATH1003 (11:40 - 13:10 PM) , CSE1021 (14:50- 16:20 PM) ",
    "SAT": "Sports / Club Activities"
}

faculty_courses = ["Python", "Physics"]
students_under_faculty = ["Aarav", "Diya", "Kabir","Avni","Rahul","Shubh",'Prajikta']

parent_child_name = "Aarav Singh"
parent_overall_att = 90.40

alumni_passout_year = 2024
alumni_branch = "CSE"
alumni_events = ["Alumni Meetup 2025", "Ideas & Innovation Talks"]

print("====================================")
print("            VTOP SYSTEM             ")
print("====================================")

logged_in = False
role = ""

while logged_in == False:
    print("\nLogin as:")
    print("1. Student")
    print("2. Employee")
    print("3. Parent")
    print("4. Alumni")
    
    r = input("Enter login as :")

    if r == "1":
        role = "student"
    elif r == "2":
        role = "employee"
    elif r == "3":
        role = "parent"
    elif r == "4":
        role = "alumni"
    else:
        print("Invalid role! Try again.")
        continue

    reg = input("Enter Username: ")
    pas = input("Enter Password: ")

    if reg == users[role]["reg"] and pas == users[role]["pass"]:
        print("\nLogin Successful!\nWelcome,", users[role]["name"])
        logged_in = True
    else:
        print("\nInvalid credentials. Try again.\n")


choice = ""

while choice != "0":
    print("\n=========== MAIN MENU ===========")
    
    if role == "student":
        print("1. View Attendance")
        print("2. View Marks")
        print("3. View Timetable")  
    
    elif role == "employee":
        print("1. View Courses Assigned")
        print("2. View Students Under You")
    
    elif role == "parent":
        print("1. View Child Name")
        print("2. View Child Attendance")
    
    elif role == "alumni":
        print("1. View Passout Details")
        print("2. View Alumni Events")

    print("0. Logout")

    choice = input("Enter choice: ")

    if role == "student":
        if choice == "1":
            print("\n---- Attendance ----")
            for sub in attendance:
                print(sub, ":", attendance[sub], "%")

        elif choice == "2":
            print("\n---- Marks ----")
            for sub in marks:
                print(sub, ":", marks[sub], "/50")

        elif choice == "3":
            print("\n---- Weekly Timetable ----")
            for day in timetable:
                print(day, ":", timetable[day])

    elif role == "employee":
        if choice == "1":
            print("\n---- Courses Assigned ----")
            for c in faculty_courses:
                print(c)

        elif choice == "2":
            print("\n---- Students Under Faculty ----")
            for s in students_under_faculty:
                print(s)

    elif role == "parent":
        if choice == "1":
            print("\nChild Name:", parent_child_name)
        elif choice == "2":
            print("\nOverall Attendance:", parent_overall_att, "%")

    elif role == "alumni":
        if choice == "1":
            print("\nPassout Year:", alumni_passout_year)
            print("Branch:", alumni_branch)
        elif choice == "2":
            print("\n---- Alumni Events ----")
            for e in alumni_events:
                print(e)

    elif choice == "0":
        print("\nLogged out successfully.")
    else:
        print("\nInvalid choice! Try again."

