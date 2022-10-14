<template>
  <div class="columns is-multiline" v-if="tasks.length">
    <TaskCard
      @removerTask="removerTask"
      v-for="task in tasks"
      :key="task.name"
      :task="task"
      @click="mudarEstado(task)"/>
  </div>
  <div class="columns is-centered" v-else>
    <h4 class="title is-4">Nenhuma tarefa pendente.</h4>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TaskCard from './TaskCard.vue';
import ITask from '../interfaces/ITask';

export default defineComponent({
  name: 'TaskGrid',
  props: {
    tasks: { type: Array as ()=> ITask[], required: true },
  },
  components: { TaskCard },
  methods: {
    removerTask(task : ITask) {
      this.$emit('removerTask', task);
    },
    mudarEstado(task: ITask) {
      this.$emit('mudarEstado', task);
    },
  },
});

</script>

<style>
</style>
