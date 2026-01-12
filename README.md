<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Student Registration</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f6f8;
            padding: 20px;
        }

        h2 {
            text-align: center;
        }

        .container {
            max-width: 700px;
            margin: auto;
            background: #fff;
            padding: 20px;
            border-radius: 6px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }

        input {
            width: 100%;
            padding: 8px;
            margin: 6px 0;
        }

        button {
            padding: 8px 12px;
            margin-top: 10px;
            cursor: pointer;
            border: none;
            border-radius: 4px;
        }

        .btn-add {
            background: #28a745;
            color: white;
        }

        .btn-edit {
            background: #007bff;
            color: white;
        }

        .btn-delete {
            background: #dc3545;
            color: white;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        table, th, td {
            border: 1px solid #ccc;
        }

        th, td {
            padding: 10px;
            text-align: center;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Student Registration</h2>

    <input type="hidden" id="editIndex">

    <label>Name</label>
    <input type="text" id="name" placeholder="Enter name">

    <label>Email</label>
    <input type="email" id="email" placeholder="Enter email">

    <label>Course</label>
    <input type="text" id="course" placeholder="Enter course">

    <button class="btn-add" onclick="addStudent()">Save Student</button>

    <table>
        <thead>
            <tr>
                <th>Name</th>
                <th>Email</th>
                <th>Course</th>
                <th>Actions</th>
            </tr>
        </thead>
        <tbody id="studentTable"></tbody>
    </table>
</div>

<script>
    let students = [];

    function addStudent() {
        let name = document.getElementById("name").value;
        let email = document.getElementById("email").value;
        let course = document.getElementById("course").value;
        let editIndex = document.getElementById("editIndex").value;

        if (name === "" || email === "" || course === "") {
            alert("Please fill all fields");
            return;
        }

        if (editIndex === "") {
            students.push({ name, email, course });
        } else {
            students[editIndex] = { name, email, course };
            document.getElementById("editIndex").value = "";
        }

        clearForm();
        displayStudents();
    }

    function displayStudents() {
        let table = document.getElementById("studentTable");
        table.innerHTML = "";

        students.forEach((student, index) => {
            table.innerHTML += `
                <tr>
                    <td>${student.name}</td>
                    <td>${student.email}</td>
                    <td>${student.course}</td>
                    <td>
                        <button class="btn-edit" onclick="editStudent(${index})">Edit</button>
                        <button class="btn-delete" onclick="deleteStudent(${index})">Delete</button>
                    </td>
                </tr>
            `;
        });
    }

    function editStudent(index) {
        document.getElementById("name").value = students[index].name;
        document.getElementById("email").value = students[index].email;
        document.getElementById("course").value = students[index].course;
        document.getElementById("editIndex").value = index;
    }

    function deleteStudent(index) {
        if (confirm("Are you sure you want to delete this student?")) {
            students.splice(index, 1);
            displayStudents();
        }
    }

    function clearForm() {
        document.getElementById("name").value = "";
        document.getElementById("email").value = "";
        document.getElementById("course").value = "";
    }
</script>

</body>
</html>
# Nishanthini-naan-mdhavan
NM 
