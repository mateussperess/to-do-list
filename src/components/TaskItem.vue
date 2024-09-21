<template>
  <li class="flex items-center justify-between p-3 mb-2 border-b border-gray-200 last:border-none">
    <div class="flex items-center">
      <div class="flex items-center">
        <input type="checkbox" :checked="task.completed" @change="changeStatus" class="size-4 rounded border-gray-300">
      </div>
      <span :class="{
          'line-through text-gray-400': task.completed,
          'text-gray-800': !task.completed,
        }" class="text-lg px-8"> 
        {{ task.text }} 
      </span>
    </div>
    
    <div>
      <button type="button" class="text-yellow-400 hover:text-white border border-yellow-400 hover:bg-yellow-500 focus:ring-4 focus:outline-none focus:ring-yellow-300 font-medium rounded-lg text-sm px-2.5 py-2.5 text-center me-2 mb-2 dark:border-yellow-300 dark:text-yellow-300 dark:hover:text-white dark:hover:bg-yellow-400 dark:focus:ring-yellow-900">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="m16.862 4.487 1.687-1.688a1.875 1.875 0 1 1 2.652 2.652L10.582 16.07a4.5 4.5 0 0 1-1.897 1.13L6 18l.8-2.685a4.5 4.5 0 0 1 1.13-1.897l8.932-8.931Zm0 0L19.5 7.125M18 14v4.75A2.25 2.25 0 0 1 15.75 21H5.25A2.25 2.25 0 0 1 3 18.75V8.25A2.25 2.25 0 0 1 5.25 6H10" />
        </svg>
      </button>

  
      <button @click="removeTask" class="text-red-700 hover:text-white border border-red-700 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-red-300 font-medium rounded-lg text-sm px-2.5 py-2.5 text-center me-2 mb-2 dark:border-red-500 dark:text-red-500 dark:hover:text-white dark:hover:bg-red-600 dark:focus:ring-red-900">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6">
          <path stroke-linecap="round" stroke-linejoin="round" d="m9.75 9.75 4.5 4.5m0-4.5-4.5 4.5M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
        </svg>
      </button>
    </div>
  </li>
</template>

<script>
  export default {
    name: 'TaskItem',
    props: {
      task: {
        type: Object,
        required: true
      }
    },
    methods: {
      removeTask() {
        this.$emit('removeTask');
      },
      changeStatus() {
        this.$emit('changeStatus');
      }
    }  
  };
</script>

<style scoped></style>