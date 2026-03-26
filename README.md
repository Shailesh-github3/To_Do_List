[# Ex03 To-Do List using JavaScript
## Date: 10/03/2026
## Reg : 212224220093

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Advanced To-Do App</title>

<style>

body{
    font-family: Arial;
    background: linear-gradient(135deg,#667eea,#764ba2);
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
}

.container{
    background:white;
    padding:30px;
    width:420px;
    border-radius:10px;
    box-shadow:0 10px 25px rgba(0,0,0,0.2);
}

h1{
    text-align:center;
}

.input-section{
    display:flex;
    gap:10px;
    margin-bottom:20px;
}

input{
    flex:1;
    padding:10px;
    border-radius:5px;
    border:1px solid #ccc;
}

button{
    padding:10px;
    border:none;
    border-radius:5px;
    cursor:pointer;
}

.add{
    background:#667eea;
    color:white;
}

.complete{
    background:#2ecc71;
    color:white;
}

.delete{
    background:#e74c3c;
    color:white;
}

ul{
    list-style:none;
    padding:0;
}

li{
    display:flex;
    justify-content:space-between;
    align-items:center;
    padding:10px;
    margin-bottom:10px;
    background:#f1f1f1;
    border-radius:5px;
}

.completed{
    text-decoration:line-through;
    color:gray;
}

.counter{
    text-align:center;
    margin-top:15px;
}

</style>
</head>

<body>

<div class="container">

<h1>To-Do App</h1>

<div class="input-section">
<input type="text" id="taskInput" placeholder="Enter task">
<button class="add" onclick="addTask()">Add</button>
</div>

<ul id="taskList"></ul>

<div class="counter">
Completed: <span id="completed">0</span> |
Pending: <span id="pending">0</span>
</div>

</div>

<script>

let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

function saveTasks(){
    localStorage.setItem("tasks",JSON.stringify(tasks));
}

function addTask(){

    const input=document.getElementById("taskInput");
    const text=input.value.trim();

    if(text===""){
        alert("Enter a task");
        return;
    }

    tasks.push({text:text,done:false});

    input.value="";

    saveTasks();
    renderTasks();
}

function completeTask(index){

    tasks[index].done = !tasks[index].done;

    saveTasks();
    renderTasks();
}

function deleteTask(index){

    tasks.splice(index,1);

    saveTasks();
    renderTasks();
}

function renderTasks(){

    const list=document.getElementById("taskList");
    list.innerHTML="";

    let completed=0;

    tasks.forEach((task,index)=>{

        const li=document.createElement("li");

        if(task.done){
            li.classList.add("completed");
            completed++;
        }

        const text=document.createElement("span");
        text.textContent=task.text;

        const btnGroup=document.createElement("div");

        const completeBtn=document.createElement("button");
        completeBtn.textContent="✓";
        completeBtn.className="complete";
        completeBtn.onclick=function(){
            completeTask(index);
        };

        const deleteBtn=document.createElement("button");
        deleteBtn.textContent="✕";
        deleteBtn.className="delete";
        deleteBtn.onclick=function(){
            deleteTask(index);
        };

        btnGroup.appendChild(completeBtn);
        btnGroup.appendChild(deleteBtn);

        li.appendChild(text);
        li.appendChild(btnGroup);

        list.appendChild(li);

    });

    document.getElementById("completed").textContent=completed;
    document.getElementById("pending").textContent=tasks.length-completed;
}

document.getElementById("taskInput").addEventListener("keypress",function(e){
    if(e.key==="Enter"){
        addTask();
    }
});

renderTasks();

</script>

</body>
</html>
```

## OUTPUT
<img width="1624" height="823" alt="image" src="https://github.com/user-attachments/assets/633d3c20-7851-4a06-b0d8-46d916e3693c" />

## Live Site:

[Live WebSite](https://jothilakshmi12.github.io/To_Do_List/)

## RESULT
The program for creating To-do list using JavaScript is executed successfully.
](https://github.com/selvasachein/To_Do_List)
