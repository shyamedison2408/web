<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Job Application Form</title>
    <style>
        body { font-family: Arial, sans-serif; }
        .container { width: 50%; margin: auto; }
        .input-control { margin-bottom: 10px; }
        .error { color: red; font-size: 14px; }
        .input-control input { width: 100%; padding: 8px; margin-top: 5px; }
        .success { border: 2px solid green; }
        .error-input { border: 2px solid red; }
        button { background: black; color: white; padding: 10px 15px; border: none; cursor: pointer; }
    </style>
</head>
<body>

<div class="container">
    <h2>Submit your application</h2>
    <form id="jobForm">
        <div class="input-control">
            <label>Name (as per ID proof)*</label>
            <input type="text" id="name">
            <span class="error" id="nameError"></span>
        </div>

        <div class="input-control">
            <label>Father's Name*</label>
            <input type="text" id="fatherName">
            <span class="error" id="fatherNameError"></span>
        </div>

        <div class="input-control">
            <label>Email*</label>
            <input type="text" id="email">
            <span class="error" id="emailError"></span>
        </div>

        <div class="input-control">
            <label>Date of Birth*</label>
            <input type="date" id="dob">
            <span class="error" id="dobError"></span>
        </div>

        <div class="input-control">
            <label>Mobile No*</label>
            <input type="text" id="mobile">
            <span class="error" id="mobileError"></span>
        </div>

        <div class="input-control">
            <label>Current Address</label>
            <input type="text" id="address">
        </div>

        <div class="input-control">
            <label>Permanent Address</label>
            <input type="text" id="permanentAddress">
        </div>

        <div class="input-control">
            <label>City</label>
            <input type="text" id="city">
        </div>

        <div class="input-control">
            <label>State</label>
            <input type="text" id="state">
        </div>

        <div class="input-control">
            <label>Zip Code</label>
            <input type="text" id="zipCode">
        </div>

        <div class="input-control">
            <label>Upload Photo</label>
            <input type="file" id="photo">
        </div>

        <button type="submit">Submit</button>
    </form>
</div>

<script>
    document.getElementById("jobForm").addEventListener("submit", function (e) {
        e.preventDefault(); // Prevent form submission

        let isValid = true;

        // Get input values
        const name = document.getElementById("name").value.trim();
        const fatherName = document.getElementById("fatherName").value.trim();
        const email = document.getElementById("email").value.trim();
        const dob = document.getElementById("dob").value;
        const mobile = document.getElementById("mobile").value.trim();

        // Regex patterns
        const nameRegex = /^[a-zA-Z\s]+$/;
        const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
        const mobileRegex = /^[0-9]{10}$/;

        // Validate Name
        if (!name.match(nameRegex)) {
            showError("nameError", "Only letters and spaces allowed.");
            isValid = false;
        } else {
            showSuccess("nameError", "name");
        }

        // Validate Father's Name
        if (!fatherName.match(nameRegex)) {
            showError("fatherNameError", "Only letters and spaces allowed.");
            isValid = false;
        } else {
            showSuccess("fatherNameError", "fatherName");
        }

        // Validate Email
        if (!email.match(emailRegex)) {
            showError("emailError", "Enter a valid email.");
            isValid = false;
        } else {
            showSuccess("emailError", "email");
        }

        // Validate DOB
        if (!dob) {
            showError("dobError", "Date of birth is required.");
            isValid = false;
        } else {
            showSuccess("dobError", "dob");
        }

        // Validate Mobile Number
        if (!mobile.match(mobileRegex)) {
            showError("mobileError", "Enter a valid 10-digit mobile number.");
            isValid = false;
        } else {
            showSuccess("mobileError", "mobile");
        }

        // Submit if all fields are valid
        if (isValid) {
            alert("Form submitted successfully!");
            document.getElementById("jobForm").reset();
        }
    });

    function showError(errorId, message) {
        document.getElementById(errorId).innerText = message;
        document.getElementById(errorId.replace("Error", "")).classList.add("error-input");
    }

    function showSuccess(errorId, inputId) {
        document.getElementById(errorId).innerText = "";
        document.getElementById(inputId).classList.remove("error-input");
        document.getElementById(inputId).classList.add("success");
    }
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 500px;
            margin: 20px auto;
            padding: 20px;
        }

        .container {
            background-color: #f9f9f9;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .input-group {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        input[type="text"] {
            flex: 1;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        button {
            padding: 8px 16px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        button:hover {
            background-color: #45a049;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            display: flex;
            align-items: center;
            padding: 10px;
            background-color: white;
            margin-bottom: 8px;
            border-radius: 4px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }

        .delete-btn {
            margin-left: auto;
            background-color: #ff4444;
        }

        .delete-btn:hover {
            background-color: #cc0000;
        }

        .completed {
            text-decoration: line-through;
            opacity: 0.7;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Todo List</h1>
        <div class="input-group">
            <input type="text" id="todoInput" placeholder="Add a new task...">
            <button onclick="addTodo()">Add</button>
        </div>
        <ul id="todoList"></ul>
    </div>

    <script>
        // Load todos from localStorage when page loads
        document.addEventListener('DOMContentLoaded', loadTodos);

        function addTodo() {
            const input = document.getElementById('todoInput');
            const text = input.value.trim();
            
            if (text === '') return;

            const todo = {
                id: Date.now(),
                text: text,
                completed: false
            };

            addTodoToList(todo);
            saveTodos();
            input.value = '';
        }

        function addTodoToList(todo) {
            const list = document.getElementById('todoList');
            
            const li = document.createElement('li');
            li.dataset.id = todo.id;
            
            li.innerHTML = `
                <input type="checkbox" ${todo.completed ? 'checked' : ''}>
                <span class="${todo.completed ? 'completed' : ''}">${todo.text}</span>
                <button class="delete-btn" onclick="deleteTodo(${todo.id})">Delete</button>
            `;

            li.querySelector('input').addEventListener('change', toggleTodo);
            list.appendChild(li);
        }

        function deleteTodo(id) {
            const li = document.querySelector(`li[data-id="${id}"]`);
            li.remove();
            saveTodos();
        }

        function toggleTodo(e) {
            const span = e.target.nextElementSibling;
            span.classList.toggle('completed');
            saveTodos();
        }

        function saveTodos() {
            const todos = [];
            document.querySelectorAll('li').forEach(li => {
                todos.push({
                    id: parseInt(li.dataset.id),
                    text: li.querySelector('span').textContent,
                    completed: li.querySelector('input').checked
                });
            });
            localStorage.setItem('todos', JSON.stringify(todos));
        }

        function loadTodos() {
            const todos = JSON.parse(localStorage.getItem('todos') || '[]');
            todos.forEach(todo => addTodoToList(todo));
        }

        // Handle Enter key press
        document.getElementById('todoInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') addTodo();
        });
    </script>
</body>
</html>
