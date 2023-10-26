<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <style>body,
        h1,
        h2,
        ul {
          margin: 0;
          padding: 0;
        }
        
        body {
          background-image: url("list.jpg");
          background-size: cover;
          font-family: "Montserrat", sans-serif;
          margin: 0;
          padding: 0;
          background-color: rgba(0, 0, 0, 0.2);
        }
        
        header {
          background-color: rgba(15, 47, 68, 0.8);
          color: #fff;
          padding: 20px 0;
          text-align: center;
          font-family: "Montserrat", sans-serif;
        }
        
        header h1 {
          font-size: 50px;
          margin: 5;
        }
        
        .add-task {
          display: flex;
          justify-content: center;
          align-items: center;
          margin-top: 30px;
        }
        
        .add-task input[type="text"],
        .add-task input[type="date"],
        .add-task button {
          padding: 15px;
          font-size: 20px;
          border: none;
          border-radius: 10px;
          margin: 10px;
        }
        
        .add-task input[type="text"] {
          width: 200px;
        }
        
        .add-task button {
          background-color: #2e3e5c;
          color: #fff;
          cursor: pointer;
          transition: background-color 0.3s, transform 0.2s;
        }
        
        .add-task button:hover {
          background-color: #410958;
          transform: scale(1.05);
        }
        
        .task-list {
          text-align: center;
          margin-top: 20px;
        }
        
        .task-list h2 {
          background-color: burlywood;
          text-align: center;
          font-size: 30px;
          padding: 20px;
          border-radius: 10px;
          margin: 20px;
          display: inline-block;
        }
        
        ul#tasks {
          list-style: none;
          padding: 0;
        }
        
        li {
          background-color: rgba(234, 231, 231, 0.95);
          color: #333;
          padding: 20px;
          border-radius: 10px;
          margin: 20px;
          display: flex;
          justify-content: space-between;
          align-items: center;
          box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        
        .completed {
          text-decoration: line-through;
          opacity: 0.5;
        }
    </style>
    <div> 
         <header>
        <h1>To-Do List</h1>
    </header>
    <div class="add-task">
        <input type="text" id="taskName" placeholder="Task name">
        <input type="text" id="taskPriority" placeholder="Priority">
        <input type="date" id="taskDueDate">
        <button onclick="addTask()">Add Task</button>
    </div>
    <div class="task-list">
        <h2>Task List</h2>
        <ul id="tasks"></ul>
    </div>
    <script>const taskNameInput = document.getElementById("taskName");
        const taskPriorityInput = document.getElementById("taskPriority");
        const taskDueDateInput = document.getElementById("taskDueDate");
        const tasksList = document.getElementById("tasks");
        
        function addTask() {
            const taskName = taskNameInput.value;
            const taskPriority = taskPriorityInput.value;
            const taskDueDate = taskDueDateInput.value;
        
            if (taskName.trim() === "") {
                alert("Task name cannot be empty.");
                return;
            }
        
            const taskItem = document.createElement("li");
            taskItem.innerHTML = `
                ${taskName} - Priority: ${taskPriority} - Due Date: ${taskDueDate}
                <button onclick="completeTask(this)">Complete</button>
                <button onclick="deleteTask(this)">Delete</button>
            `;
        
            tasksList.appendChild(taskItem);
        
            // Clear input fields
            taskNameInput.value = "";
            taskPriorityInput.value = "";
            taskDueDateInput.value = "";
        }
        
        function completeTask(button) {
            const taskItem = button.parentElement;
            taskItem.classList.toggle("completed");
        }
        
        function deleteTask(button) {
            const taskItem = button.parentElement;
            taskItem.remove();
        }</script>
</div>
</body>
</html>
