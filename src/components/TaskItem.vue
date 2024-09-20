<template>
  <li class="flex items-center justify-between p-3 mb-2 border-b border-gray-200 last:border-none">
    <div class="flex items-center">
      <input type="checkbox" :checked="task.completed" @change="changeStatus" class="mr-2 h-5 w-5 text-blue-500 border-gray-300 rounded focus:ring focus:ring-blue-300">
      <span :class="{
          'line-through text-gray-400': task.completed,
          'text-gray-800': !task.completed,
        }" class="text-lg"> 
        {{ task.text }} 
      </span>
    </div>
    <button @click="removeTask" class="px-2 py-1 text-sm bg-red-500 text-white rounded hover:bg-red-600 focus:outline-none focus:ring focus:ring-red-300"> X </button>
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