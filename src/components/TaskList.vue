<template>
  <div class="list-container">
    <div class="p-4 bg-white rounded-lg shadow-lg">
      <h1 class="text-center text-5xl m-4 font-extrabold underline underline-offset-3 decoration-8 decoration-blue-400 dark:decoration-blue-600"> To-do List </h1>
      <form @submit.prevent="addTask" class="mb-4 flex">
        <input 
          type="text" 
          placeholder="Add task..."
          v-model="newTask"
          class="flex-grow px-3 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring focus:border-blue-300"      
        />
        <button type="submit" class="ml-3 px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600 focus:outline-none focus:ring focus:ring-blue-300"> Add task </button>
      </form>
    
      <ul>
        <TaskItem 
          v-for="(task, index) in tasks"
          :key="index"
          :task="task"
          @removeTask="removeTask(index)"
          @changeStatus="changeStatus(index)"
        />  
      </ul>
    </div>
  </div>
</template>

<script>
  import TaskItem from './TaskItem.vue';

  export default {
    name: 'TaskList',
    components: {
      TaskItem
    },
    data() {
      return {
        newTask: '',
        tasks: []
      }
    },
    methods: {
      addTask() {
        if (this.newTask.trim() != '') {
          this.tasks.push({ text: this.newTask, completed: false });
          this.newTask = '';
        }
      },
      removeTask(index) {
        this.tasks.splice(index, 1);
      },
      changeStatus(index) {
        this.tasks[index].completed = !this.tasks[index].completed;
      }
    }
  };
</script>

<style scoped>
  .list-container {
    max-width: 800px;
    margin: 0 auto;
  }
</style>