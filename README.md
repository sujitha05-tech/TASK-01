Sure! Here's the complete code for a To-Do List application with HTML, CSS, and JavaScript combined in one program:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .todo-container {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            margin-bottom: 20px;
            text-align: center;
        }
        .input-container {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
        }
        .input-container input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-right: 10px;
        }
        .input-container button {
            padding: 10px 20px;
            border: none;
            background-color: #5cb85c;
            color: white;
            border-radius: 4px;
            cursor: pointer;
        }
        .input-container button:hover {
            background-color: #4cae4c;
        }
        .todo-list {
            list-style-type: none;
            padding: 0;
        }
        .todo-list li {
            padding: 10px;
            border-bottom: 1px solid #ddd;
            display: flex;
            justify-content: space-between;
        }
        .todo-list li:last-child {
            border-bottom: none;
        }
        .todo-list button {
            background-color: #d9534f;
            border: none;
            color: white;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
        }
        .todo-list button:hover {
            background-color: #c9302c;
        }
    </style>
</head>
<body>
    <div class="todo-container">
        <h2>To-Do List</h2>
        <div class="input-container">
            <input type="text" id="taskInput" placeholder="Add a new task">
            <button onclick="addTask()">Add</button>
        </div>
        <ul class="todo-list" id="todoList"></ul>
    </div>

    <script>
        function addTask() {
            const taskInput = document.getElementById('taskInput');
            const taskText = taskInput.value.trim();
            if (taskText === '') return;

            const todoList = document.getElementById('todoList');
            const li = document.createElement('li');
            li.innerHTML = `${taskText} <button onclick="deleteTask(this)">Delete</button>`;
            todoList.appendChild(li);

            taskInput.value = '';
        }

        function deleteTask(button) {
            const li = button.parentElement;
            li.remove();
        }
    </script>
</body>
</html>
```

### Explanation:

1. **HTML Structure**:
    - The `div` with the class `todo-container` contains all elements of the To-Do list application.
    - Inside it, there’s an `h2` tag for the title, an `input-container` for the input field and the "Add" button, and a `ul` element with the class `todo-list` where tasks will be listed.

2. **CSS Styling**:
    - The body is styled to center the content vertically and horizontally with a light background.
    - The `.todo-container` is styled with padding, a white background, rounded corners, and a shadow for a card-like appearance.
    - Buttons and input fields are styled for better appearance and usability.

3. **JavaScript Functionality**:
    - `addTask()`: This function is called when the "Add" button is clicked. It retrieves the value from the input field, creates a new `li` element with the task and a "Delete" button, then appends it to the `ul` element.
    - `deleteTask(button)`: This function is called when a "Delete" button is clicked. It removes the corresponding `li` element from the DOM.

### Conclusion

This code snippet combines HTML, CSS, and JavaScript into a single file to create a simple, functional To-Do List application. You can add tasks using the input field and the "Add" button, and remove tasks with the "Delete" button next to each task. This is a fundamental example of how these three web technologies can work together to create interactive web applications.
