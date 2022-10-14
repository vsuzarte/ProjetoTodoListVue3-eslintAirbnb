<template>
  <main class="container">
    <div class="section">
      <div class="columns is-gapless is-centered">
        <h2 class="title is-2">Todo List</h2>
      </div>
      <ProgressBar :progresso="progresso"></ProgressBar>
      <NewTask @taskAdd="addTask"/>
      <TaskGrid
        :tasks="tasks"
        @removerTask="removerTask"
        @mudarEstado="mudarEstado"
      />
      <InfoList/>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import NewTask from './components/NewTask.vue';
import TaskGrid from './components/TaskGrid.vue';
import ITask from './interfaces/ITask';
import ProgressBar from './components/ProgressBar.vue';
import InfoList from './components/InfoList.vue';

export default defineComponent({
  name: 'App',
  components: {
    NewTask, TaskGrid, ProgressBar, InfoList,
  },
  data() {
    return {
      tasks: [] as ITask[],
      progressoTarefas: 0,
    };
  },
  computed: {
    progresso() : number {
      const total = this.tasks.length;
      const done = this.tasks.filter((e) => !e.pending).length;
      return Math.round((done / total) * 100) || 0;
    },
  },
  watch: {
    tasks: {
      handler(newValue, oldValue) {
        localStorage.setItem('tasks', JSON.stringify(this.tasks));
      },
      deep: true,
    },
  },
  methods: {
    addTask(task: ITask) {
      const newTask = !this.tasks.find((el) => el.name === task.name);
      if (newTask && task.name !== '') {
        this.tasks.push({ name: task.name, pending: task.pending || true });
      }
    },
    removerTask(task : ITask) {
      const index = this.tasks.indexOf(task);
      if (index >= 0) {
        this.tasks.splice(index, 1);
      }
    },
    mudarEstado(task: ITask) {
      this.tasks[this.getIndexTask(task)].pending = !this.tasks[this.getIndexTask(task)].pending;
    },
    getIndexTask(task: ITask) : number {
      return this.tasks.indexOf(task);
    },
  },
  created() {
    console.log('criado');
    const localJson = localStorage.getItem('tasks') || '';
    console.log(localJson);
    const array = JSON.parse(localJson);
    this.tasks = Array.isArray(array) ? array : [];
  },
});
</script>

<style>
  #app{
    background: #E0EAFC;
    background: -webkit-linear-gradient(to top, #CFDEF3, #E0EAFC);
    background: linear-gradient(to top, #CFDEF3, #E0EAFC);
    height: 100vh;
  }
</style>
