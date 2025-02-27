<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
    <div class="container">
        <h2>Student Grading System</h2>
        <input type="text" id="studentName" placeholder="Enter Student Name">
        <input type="number" id="studentMarks" placeholder="Enter Marks (0-100)">
        <button onclick="addStudent()">Add Student</button>

        <table>
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Marks</th>
                    <th>Grade</th>
                </tr>
            </thead>
        </table>
    </div>

    <script>
        function calculateGrade(marks) {
            if (marks >= 90) return 'A+';
            else if (marks >= 80) return 'A';
            else if (marks >= 70) return 'B';
            else if (marks >= 60) return 'C';
            else if (marks >= 50) return 'D';
            else return 'F';
        }

        function addStudent() {
            let name = document.getElementById("studentName").value.trim();
            let marks = document.getElementById("studentMarks").value.trim();
            
            if (name === "" || marks === "" || marks < 0 || marks > 100) {
                alert("Please enter a valid name and marks between 0-100.");
                return;
            }

            let grade = calculateGrade(marks);
            let table = document.getElementById("studentTable");
            let row = `<tr>
                        <td>${name}</td>
                        <td>${marks}</td>
                        <td>${grade}</td>
                       </tr>`;
            table.innerHTML += row;

            // Clear inputs
            document.getElementById("studentName").value = "";
            document.getElementById("studentMarks").value = "";
        }
    </script>
</body>
</html>
            
            
