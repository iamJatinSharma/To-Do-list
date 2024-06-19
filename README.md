# To-Do-list
I recently built a to-do list using HTML, CSS, and JavaScript. This project allowed me to combine the foundational aspects of web development to create a practical application.  

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 800px;
            margin: 50px auto;
            padding: 20px;
            background: white;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }

        h1 {
            text-align: center;
            margin-bottom: 20px;
        }

        .task-entry {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .task-entry input, .task-entry select, .task-entry button {
            padding: 10px;
            font-size: 16px;
        }

        .task-list h2 {
            margin-bottom: 10px;
        }

        .task-list ul {
            list-style-type: none;
            padding: 0;
        }

        .task-list ul li {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 10px;
            background: #f9f9f9;
            margin-bottom: 5px;
            border: 1px solid #ddd;
        }

        .task-list ul li.completed {
            text-decoration: line-through;
            color: #888;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>To-Do List</h1>
        <div class="task-entry">
            <input type="text" id="task-input" placeholder="Enter a new task">
            <input type="date" id="due-date">
            <select id="priority">
                <option value="low">Low Priority</option>
                <option value="medium">Medium Priority</option>
                <option value="high">High Priority</option>
            </select>
            <select id="category">
                <option value="work">Work</option>
                <option value="personal">Personal</option>
                <option value="other">Other</option>
            </select>
            <button id="add-task-button">Add Task</button>
        </div>
        <div class="task-list">
            <h2>Tasks</h2>
            <ul id="tasks">
                <!-- Tasks will be added here dynamically -->
            </ul>
        </div>
    </div>
    <script>
        document.getElementById('add-task-button').addEventListener('click', addTask);

        function addTask() {
            const taskInput = document.getElementById('task-input');
            const dueDateInput = document.getElementById('due-date');
            const priorityInput = document.getElementById('priority');
            const categoryInput = document.getElementById('category');

            const taskText = taskInput.value.trim();
            const dueDate = dueDateInput.value;
            const priority = priorityInput.value;
            const category = categoryInput.value;

            if (taskText !== '') {
                const taskList = document.getElementById('tasks');
                const taskItem = document.createElement('li');

                taskItem.innerHTML = `
                    <span>${taskText} - ${category} - ${priority} - ${dueDate}</span>
                    <div>
                        <button onclick="completeTask(this)">Complete</button>
                        <button onclick="deleteTask(this)">Delete</button>
                    </div>
                `;

                taskList.appendChild(taskItem);
                taskInput.value = '';
                dueDateInput.value = '';
                priorityInput.value = 'low';
                categoryInput.value = 'work';
            }
        }

        function completeTask(button) {
            const taskItem = button.parentNode.parentNode;
            taskItem.classList.toggle('completed');
        }

        function deleteTask(button) {
            const taskItem = button.parentNode.parentNode;
            taskItem.remove();
        }
    </script>
</body>
</html>
