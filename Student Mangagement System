-- Create Students table
CREATE TABLE Students (
  StudentID INT PRIMARY KEY,
  Name VARCHAR(50),
  Class VARCHAR(20)
);

-- Create Classes table
CREATE TABLE Classes (
  ClassID INT PRIMARY KEY,
  ClassName VARCHAR(50),
  ClassDate DATE
);

-- Create Attendance table
CREATE TABLE Attendance (
  AttendanceID INT PRIMARY KEY,
  StudentID INT,
  ClassID INT,
  Status VARCHAR(10), -- Present or Absent
  FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
  FOREIGN KEY (ClassID) REFERENCES Classes(ClassID)
);

-- Insert sample data
INSERT INTO Students VALUES (1, 'Alice', '10A');
INSERT INTO Classes VALUES (101, 'Math', '2025-08-13');
INSERT INTO Attendance VALUES (1001, 1, 101, 'Present');

-- Sample Query: List students and their attendance status for a class
SELECT s.Name, c.ClassName, a.Status
FROM Attendance a
JOIN Students s ON a.StudentID = s.StudentID
JOIN Classes c ON a.ClassID = c.ClassID
WHERE c.ClassDate = '2025-08-13';

-- Sample Query: Calculate attendance percentage for a student
SELECT s.Name,
  (SUM(CASE WHEN a.Status = 'Present' THEN 1 ELSE 0 END) * 100.0) / COUNT(*) AS AttendancePercentage
FROM Attendance a
JOIN Students s ON a.StudentID = s.StudentID
GROUP BY s.StudentID, s.Name;
