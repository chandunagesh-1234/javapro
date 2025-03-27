
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f2f2f2;
        }

        h1 {
            text-align: center;
            color: #4CAF50;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        th, td {
            padding: 10px;
            text-align: left;
            border: 1px solid #ddd;
        }

        th {
            background-color: #4CAF50;
            color: white;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
            background-color: white;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        input[type="text"], input[type="number"] {
            width: 100%;
            padding: 10px;
            margin: 8px 0;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        button {
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        .error {
            color: red;
        }
    </style>
</head>
<body>

    <h1>Student Grading System</h1>

    <div class="container">
        <label for="studentName">Student Name:</label>
        <input type="text" id="studentName" placeholder="Enter student name">

        <label for="studentMarks">Marks (0-100):</label>
        <input type="number" id="studentMarks" placeholder="Enter marks" min="0" max="100">

        <button onclick="addStudent()">Add Student</button>
        <p class="error" id="error"></p>
    </div>

    <table id="studentTable">
        <thead>
            <tr>
                <th>Name</th>
                <th>Marks</th>
                <th>Grade</th>
            </tr>
        </thead>
        <tbody>
            <!-- New rows will be added here -->
        </tbody>
    </table>

    <script>
        // Function to calculate the grade based on marks
        function calculateGrade(marks) {
            if (marks >= 90) return 'A+';
            else if (marks >= 80) return 'A';
            else if (marks >= 70) return 'B';
            else if (marks >= 60) return 'C';
            else if (marks >= 50) return 'D';
            else return 'F';
        }

        // Function to add a student to the table
        function addStudent() {
            let name = document.getElementById("studentName").value.trim();
            let marks = parseInt(document.getElementById("studentMarks").value.trim(), 10);
            let errorElement = document.getElementById("error");

            // Clear any previous error message
            errorElement.textContent = "";

            // Validate input
            if (name === "" || isNaN(marks) || marks < 0 || marks > 100) {
                errorElement.textContent = "Please enter a valid name and marks between 0-100.";
                return;
            }

            let grade = calculateGrade(marks);
            let table = document.getElementById("studentTable").getElementsByTagName('tbody')[0];
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
            
