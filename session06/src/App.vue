<script setup>
import { ref, onMounted } from 'vue';

// State variables
const newTask = ref('');
const tasks = ref([]);
const isEditing = ref(false);
const taskToEditId = ref(null);

// Load tasks from localStorage on mount
onMounted(() => {
  const storedTasks = JSON.parse(localStorage.getItem('tasks')) || [];
  tasks.value = storedTasks;
});

// Add or update a task
const addOrUpdateTask = () => {
  if (newTask.value.trim() === '') return;

  if (isEditing.value) {
    // Update existing task
    const task = tasks.value.find(task => task.id === taskToEditId.value);
    task.text = newTask.value;
    taskToEditId.value = null;
    isEditing.value = false;
  } else {
    // Add a new task
    tasks.value.push({
      id: Date.now(),
      text: newTask.value,
      completed: false,
    });
  }

  newTask.value = '';
  updateLocalStorage();
};

// Edit a task
const editTask = (id) => {
  const task = tasks.value.find(task => task.id === id);
  newTask.value = task.text;
  isEditing.value = true;
  taskToEditId.value = id;
};

// Delete a task
const deleteTask = (id) => {
  tasks.value = tasks.value.filter(task => task.id !== id);
  updateLocalStorage();
};

// Toggle task completion
const toggleCompletion = (id) => {
  const task = tasks.value.find(task => task.id === id);
  task.completed = !task.completed;
  updateLocalStorage();
};

// Update localStorage
const updateLocalStorage = () => {
  localStorage.setItem('tasks', JSON.stringify(tasks.value));
};
</script>


<template>
  <div class="container">
    <div class="todo">
      <h3 class="heading">Danh sách công việc</h3>
      <header class="header">
        <input
          type="text"
          v-model="newTask"
          class="input"
          placeholder="Thêm công việc mới"
        />
        <button class="button button-add" @click="addOrUpdateTask">
          {{ isEditing ? 'Cập nhật' : 'Thêm' }}
        </button>
      </header>

      <ul class="list-item">
        <li
          v-for="task in tasks"
          :key="task.id"
          class="item"
        >
          <div class="left">
            <input
              type="checkbox"
              :checked="task.completed"
              @change="toggleCompletion(task.id)"
            />
            <label
              :class="{ completed: task.completed }"
            >
              {{ task.text }}
            </label>
          </div>
          <div class="right">
            <button class="button button-edit" @click="editTask(task.id)">
              Sửa
            </button>
            <button class="button button-delete" @click="deleteTask(task.id)">
              Xóa
            </button>
          </div>
        </li>
      </ul>

      <footer class="footer">
        <p>Công việc hoàn thành:</p>
        <p>
          <b>{{ tasks.filter(task => task.completed).length }}</b> / <b>{{ tasks.length }}</b>
        </p>
      </footer>
    </div>
  </div>
</template>


<style scoped>
.container {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.heading {
  text-align: center;
  font-size: 24px;
  padding-bottom: 24px;
}

.todo {
  width: 600px;
  border: 1px solid #dadada;
  padding: 20px 24px;
  border-radius: 8px;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
}

.header {
  display: flex;
  align-items: center;
  margin-bottom: 20px;
  gap: 12px;
}

.input {
  height: 36px;
  border: 1px solid #dadada;
  outline: none;
  border-radius: 4px;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
  flex: 1;
  padding: 0 16px;
}

.button {
  height: 36px;
  border: 1px solid transparent;
  color: #fff;
  outline: none;
  border-radius: 4px;
  padding: 0 16px;
  cursor: pointer;
}

.button-add {
  background-color: blue;
}

.button-delete {
  background-color: red;
}
.button-edit{
  background-color: rgb(255, 230, 0);
}
.list-item {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 20px;
}

.item {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

input[type="checkbox"] {
  height: 18px;
  width: 18px;
}

.left {
  display: flex;
  align-items: center;
  gap: 8px;
}

.right {
  display:  flex;
  gap: 5px;
}

.footer {
  display: flex;
  gap: 8px;
}

.completed {
  text-decoration: line-through;
  color: grey;
}
</style>
