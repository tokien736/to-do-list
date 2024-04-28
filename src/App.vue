<script setup>
import { ref, onMounted, computed, watch } from 'vue'


// Ordenar las tareas por fecha de creación ascendente
const todos_asc = computed(() => todos.value.sort((a,b) => {

}))

// Observadores para guardar datos en el localStorage
watch(name, (newVal) => {

})

watch(todos, (newVal) => {

})

// Función para agregar una nueva tarea
const addTodo = () => {

}

// Función para eliminar una tarea
const removeTodo = (todo) => {

}

// Inicialización de datos al cargar la página
onMounted(() => {
   
})
</script>
<template>
  <main class="app">
      
      <!-- Sección de saludo -->
      <section class="greeting">
          <!-- Campo de entrada para el nombre del usuario -->
          <h2 class="title">
          Hola, <input type="text" id="name" placeholder="Su nombre" v-model="name">
          </h2>
      </section>
  
      <!-- Sección para crear una nueva tarea -->
      <section class="create-todo">
          <h3>CREAR UNA LISTA</h3>
  
          <!-- Formulario para agregar una nueva tarea -->
          <form id="new-todo-form" @submit.prevent="addTodo">
              <h4>¿Qué tiene en su lista de tareas?</h4>
              <!-- Campo de entrada para el contenido de la tarea -->
              <input 
                  type="text" 
                  name="content" 
                  id="content" 
                  placeholder="por ejemplo, hacer un vídeo..."
                  v-model="input_content" />
              
              <h4>Elija una categoría</h4>
              <div class="options">
  
                  <!-- Opción de categoría de negocios -->
                  <label>
                      <input 
                          type="radio" 
                          name="category" 
                          id="category1" 
                          value="business"
                          v-model="input_category" />
                      <span class="bubble business"></span>
                      <div>Negocios</div>
                  </label>
  
                  <!-- Opción de categoría personal -->
                  <label>
                      <input 
                          type="radio" 
                          name="category" 
                          id="category2" 
                          value="personal"
                          v-model="input_category" />
                      <span class="bubble personal"></span>
                      <div>Personal</div>
                  </label>
  
              </div>
  
              <!-- Botón para agregar la tarea a la lista -->
              <input type="submit" value="Añadir a lista" />
          </form>
      </section>
  
      <!-- Sección para mostrar la lista de tareas -->
      <section class="todo-list">
          <h3>LISTA DE TAREAS</h3>
          <div class="list" id="todo-list">
  
              <!-- Iteración sobre la lista de tareas y renderizado -->
              <div v-for="todo in todos_asc" :class="todo-item ${todo.done && 'done'}">
                  <label>
                      <!-- Checkbox para marcar la tarea como completada -->
                      <input type="checkbox" v-model="todo.done" />
                      <!-- Burbuja de categoría -->
                      <span :class="`bubble ${
                          todo.category == 'business' 
                              ? 'business' 
                              : 'personal'
                      }`"></span>
                  </label>
  
                  <!-- Campo de entrada para editar el contenido de la tarea -->
                  <div class="todo-content">
                      <input type="text" v-model="todo.content" />
                  </div>
  
                  <!-- Acciones para la tarea (eliminar) -->
                  <div class="actions">
                      <button class="delete" @click="removeTodo(todo)">Delete</button>
                  </div>
              </div>
  
          </div>
      </section>
  
  </main>
  
  </template>