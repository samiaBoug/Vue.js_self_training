### **Day 1: Introduction to Vue.js**

**Objective**: Understand the basics of Vue.js and set up your development environment.

#### **Activities**

1.  **Learn About Vue.js Features and Ecosystem**

    - Read the [Vue.js Introduction](https://vuejs.org/guide/introduction.html).
    - Understand what makes Vue.js different from other frameworks:
      - Reactive data binding.
      - Component-based architecture.
      - Progressive adoption (can be used for small or large projects).
      - Integration with tools like Vue Router and Pinia.

2.  **Set Up Your Development Environment**

    - Install **Node.js** if it's not already installed ([Download Node.js](https://nodejs.org/)).
    - Choose a project setup method:
      - **Vue CLI**:
        ```bash
        npm install -g @vue/cli
        vue create my-first-vue-app
        cd my-first-vue-app
        npm run serve
        ```
      - **Vite (recommended for speed)**:
        ```bash
        npm create vite@latest my-first-vue-app --template vue
        cd my-first-vue-app
        npm install
        npm run dev
        ```

3.  **Learn Vue.js Basics**

    - Explore Vue templates:
      - Syntax for HTML, directives, and data binding.
      - Read the [Essentials Guide](https://vuejs.org/guide/essentials/template-syntax.html).
    - Practice directives:
      - **`v-bind`**: Dynamically bind attributes.
      - **`v-model`**: Two-way data binding.
      - **`v-for`**: Render lists.
      - **`v-if/v-else`**: Conditional rendering.
    - Understand event handling with **`v-on`**:
      ```html
      <button @click="handleClick">Click Me</button>
      ```

4.  **Build a Simple "To-Do List" App**

    - Features:
      - Add new tasks.
      - Mark tasks as complete/incomplete.
      - Delete tasks.
    - Example structure:

```html
<template>
  <div>
    <h1>To-Do List</h1>
    <input v-model="newTask" placeholder="Add a task" />
    <button @click="addTask">Add</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <div v-if="!task.isEditing">
          <span
            @click="toggleTask(index)"
            :style="{
              textDecoration: task.done ? 'line-through' : 'none',
              cursor: 'pointer',
            }"
          >
            {{ task.text }}
          </span>
          <button @click="editTask(index)">Edit</button>
          <button @click="deleteTask(index)">Delete</button>
        </div>
        <div v-else>
          <input v-model="task.text" />
          <button @click="saveTask(index)">Save</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const newTask = ref("");
    const tasks = ref([]);

    const addTask = () => {
      if (newTask.value.trim()) {
        tasks.value.push({
          text: newTask.value,
          done: false,
          isEditing: false,
        });
        newTask.value = "";
      }
    };

    const toggleTask = (index) => {
      tasks.value[index].done = !tasks.value[index].done;
    };

    const deleteTask = (index) => {
      tasks.value.splice(index, 1);
    };

    const editTask = (index) => {
      tasks.value[index].isEditing = true;
    };

    const saveTask = (index) => {
      tasks.value[index].isEditing = false;
    };

    return {
      newTask,
      tasks,
      addTask,
      toggleTask,
      deleteTask,
      editTask,
      saveTask,
    };
  },
};
</script>
```

5. **Optional Challenge**
   - Add a feature to edit tasks in the list.

#### **Estimated Time**: 3–4 hours
