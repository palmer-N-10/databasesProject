# databasesProject
Databases Project Group 20
# Database Information: 
Program table:

ProgramName (Primary Key)
PersonInChargeName
PersonInChargeUniversityID
PersonInChargeEmail
DepartmentCode (Foreign Key referencing Department.DepartmentCode)
Department table:

DepartmentName
DepartmentCode (Primary Key)
Faculty table:

FacultyID (Primary Key)
FacultyName
FacultyEmail
FacultyRank
DepartmentCode (Foreign Key referencing Department.DepartmentCode)
Course table:

CourseID (Primary Key, composed of DepartmentCode and a 4-digit number)
CourseTitle
CourseDescription
DepartmentCode (Foreign Key referencing Department.DepartmentCode)
Section table:

SectionNumber (Primary Key, a 3-digit number)
Semester (Primary Key, one of ‘Fall’, ‘Spring’, ‘Summer’)
Year (Primary Key)
CourseID (Foreign Key referencing Course.CourseID)
FacultyID (Foreign Key referencing Faculty.FacultyID)
NumberOfStudents
LearningObjective table:

ObjectiveCode (Primary Key)
ObjectiveDescription
ProgramName (Foreign Key referencing Program.ProgramName)
SubObjective table:

SubObjectiveCode (Primary Key, composed of ObjectiveCode and a suffix)
SubObjectiveDescription
ObjectiveCode (Foreign Key referencing LearningObjective.ObjectiveCode)
ProgramCourse table:

ProgramName (Foreign Key referencing Program.ProgramName)
CourseID (Foreign Key referencing Course.CourseID)
Primary Key (ProgramName, CourseID)
ProgramCourseObjective table:

ProgramName (Foreign Key referencing Program.ProgramName)
CourseID (Foreign Key referencing Course.CourseID)
ObjectiveCode (Foreign Key referencing LearningObjective.ObjectiveCode)
Primary Key (ProgramName, CourseID, ObjectiveCode)
SectionObjective table:

SectionNumber (Foreign Key referencing Section.SectionNumber)
Semester (Foreign Key referencing Section.Semester)
Year (Foreign Key referencing Section.Year)
ObjectiveCode (Foreign Key referencing LearningObjective.ObjectiveCode)
EvaluationMethod
NumberOfStudentsMet
Primary Key (SectionNumber, Semester, Year, ObjectiveCode)

# Datbase Relationships
Program - Department: Each program is associated with one department. This is a many-to-one relationship because many programs can be run by the same department. This relationship is represented by the DepartmentCode foreign key in the Program table.

Program - LearningObjective: Each program has multiple learning objectives. This is a one-to-many relationship because one program can have multiple learning objectives. This relationship is represented by the ProgramName foreign key in the LearningObjective table.

LearningObjective - SubObjective: Each learning objective can have multiple sub-objectives. This is a one-to-many relationship because one learning objective can have multiple sub-objectives. This relationship is represented by the ObjectiveCode foreign key in the SubObjective table.

Department - Faculty: Each department has multiple faculty members. This is a one-to-many relationship because one department can have multiple faculty members. This relationship is represented by the DepartmentCode foreign key in the Faculty table.

Department - Course: Each department offers multiple courses. This is a one-to-many relationship because one department can offer multiple courses. This relationship is represented by the DepartmentCode foreign key in the Course table.

Course - Section: Each course can have multiple sections offered every semester. This is a one-to-many relationship because one course can have multiple sections. This relationship is represented by the CourseID foreign key in the Section table.

Faculty - Section: Each faculty member can be in charge of multiple sections. This is a one-to-many relationship because one faculty member can be in charge of multiple sections. This relationship is represented by the FacultyID foreign key in the Section table.

Program - Course (through ProgramCourse): Each program is associated with multiple courses, and each course can be associated with multiple programs. This is a many-to-many relationship, which is represented by the ProgramCourse junction table.

Program - Course - LearningObjective (through ProgramCourseObjective): Each pair of a program and a course is associated with multiple learning objectives. This is a many-to-many relationship, which is represented by the ProgramCourseObjective junction table.

Section - LearningObjective (through SectionObjective): Each section needs to record whether each learning objective has been met. This is a many-to-many relationship, which is represented by the SectionObjective junction table.
