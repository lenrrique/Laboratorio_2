# Laboratorio_2



En el Codigo HTML encontramos

**<!DOCTYPE html>
<html>
<head>
<title>Lista de tareas</title>
<link rel="stylesheet" type="text/css" href="estilos.css">
</head>
<body>
<h1>HAZ TU LISTA DE TAREAS</h1>
<div id="task-container">
<input type="text" id="task-input" placeholder="Agregar nueva tarea">
<button id="add-task-btn">Agregar</button>
</div>
<ul id="task-list">
<!-- Aquí se agregarán las tareas dinámicamente -->
</ul>
<script src="app.js"></script>
</body>
</html>**

en el codigo CSS encontramos

body {
    font-family: Arial, sans-serif;
    background-color: #474646;
    margin: 0;
    padding: 20px;
    }
    h1 {
    text-align: center;
    color: #c0d3ff;
    }
    #task-container {
    display: flex;
    margin-bottom: 20px;
    }
    #task-input {
    flex-grow: 1;
    padding: 10px;
    font-size: 16px;
    }
    #add-task-btn {
    padding: 10px 20px;
    background-color: #0084ff;
    border: none;
    color: #fff;
    font-size: 16px;
    cursor: pointer;
    }
    #task-list {
    list-style-type: none;
    padding: 0;
    }
    .task-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #fff;
    padding: 10px;
    margin-bottom: 10px;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }
    .task-item span {
    flex-grow: 1;
    margin-right: 10px;
    }
    .delete-btn {
    background-color: #ff0000;
    border: none;
    color: #fff;
    padding: 5px 10px;
    font-size: 14px;
    border-radius: 3px;
    cursor: pointer;
    }
    .fade-in {
    animation: fade-in 0.5s;
    }
    @keyframesfade-in {
    from {
    opacity: 0;
    transform: translateY(-10px);
    }
    to {
    opacity: 1;
    transform: translateY(0);
    }
    }

    en el codigo Javascript encontramos

    const taskInput = document.getElementById('task-input');
const addTaskBtn = document.getElementById('add-task-btn');
const taskList = document.getElementById('task-list');
// Función para agregar una nueva tarea
function addTask() {
    const taskText = taskInput.value;
    if (taskText.trim() !== '') {
    const taskItem = document.createElement('li');
    taskItem.classList.add('task-item');
    taskItem.innerHTML = `
    <span>${taskText}</span>
    <button class="delete-btn">Eliminar</button>
    `;
    taskList.appendChild(taskItem);
taskInput.value = '';
// Agregar efecto al agregar una tarea
taskItem.classList.add('fade-in');
setTimeout(() => {
taskItem.classList.remove('fade-in');
}, 500);
}
}

// Evento para agregar una tarea al hacer clic en el botón "Agregar"
addTaskBtn.addEventListener('click', addTask);

// Evento para agregar una tarea al presionar la tecla "Enter" en el campo de entrada
taskInput.addEventListener('keydown', (event) => {
    if (event.key === 'Enter') {
    addTask();
    }
    });
    // Evento para eliminar una tarea al hacer clic en el botón "Eliminar"
    taskList.addEventListener('click', (event) => {
    if (event.target.classList.contains('delete-btn')) {
    const taskItem = event.target.parentElement;
    taskList.removeChild(taskItem);
    }
    });

    
