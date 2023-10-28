<template>
    <div class="w-full h-screen bg-gray-100 pt-8">
      <div class="bg-white p-3 max-w-md mx-auto">
        <div class="text-center">
          <h1 class="text-3xl font-bold">ToDo App</h1>
          <div class="mt-4 flex">
            <input
              class="w-80 border-b-2 border-gray-500 text-black"
              type="text"
              placeholder="Enter your task here"
              v-model="newTask"
              @keyup.enter="addTask"
            />
            <button
              class="ml-2 border-2 border-green-500 p-2 text-green-500 hover:text-white hover:bg-green-500 rounded-lg flex"
              @click="addTask"
            >
              <svg
                class="h-6 w-6"
                width="24"
                height="24"
                viewBox="0 0 24 24"
                stroke-width="2"
                stroke="currentColor"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
              >
                <path stroke="none" d="M0 0h24v24H0z" />
                <circle cx="12" cy="12" r="9" />
                <line x1="15" y1="12" x2="9" y2="15" />
                <line x1="9" y1="9" x2="15" y2="15" />
              </svg>
              <span>Add</span>
            </button>
          </div>
        </div>
        <div class="mt-8">
          <ul>
            <li class="p-2 rounded-lg" v-for="(task, index) in tasks" :key="index">
              <div class="flex align-middle flex-row justify-between">
                <div class="p-2">
                  <input type="checkbox" class="h-6 w-6" v-model="task.completed" />
                </div>
                <div class="p-2">
                  <p class="text-lg" :class="{ 'line-through text-gray-400': task.completed }">{{ task.text }}</p>
                </div>
                <button
                  class="flex text-red-500 border-2 border-red-500 p-2 rounded-lg"
                  @click="removeTask(index)"
                >
                  <svg
                    class="h-6 w-6 text-red-500"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  >
                    <circle cx="12" cy="12" r="10" />
                    <line x1="15" y1="9" x2="9" y2="15" />
                    <line x1="9" y1="9" x2="15" y2="15" />
                  </svg>
                  <span>Remove</span>
                </button>
              </div>
              <hr class="mt-2" />
            </li>
          </ul>
        </div>
        <div class="mt-8">
          <button class="border-2 border-red-500 p-2 text-red-500" @click="clearCompletedTasks">Clear Completed Task</button>
          <button class="border-2 border-indigo-500 p-2 text-indigo-500 ml-4" @click="resetTasks">Reset Todo List</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: '',
        tasks: [],
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() !== '') {
          this.tasks.push({ text: this.newTask, completed: false });
          this.newTask = '';
        }
      },
      removeTask(index) {
        this.tasks.splice(index, 1);
      },
      clearCompletedTasks() {
        this.tasks = this.tasks.filter((task) => !task.completed);
      },
      resetTasks() {
        this.tasks = [];
      },
    },
  };
  </script>
  