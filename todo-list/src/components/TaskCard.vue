<template>
  <div class="column is-one-third">
    <div class="columns is-gapless">
      <div class="column is-10" :class="stateClass">
        <p class="task">{{task.name}}</p>
      </div>
      <div class="column is-2">
        <button @click.stop="removeTask" class="button is-danger is-outlined">x</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ITask from '../interfaces/ITask';

export default defineComponent({
  name: 'TaskCard',
  props: {
    task: { type: Object as ()=> ITask, required: true },
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending,
      };
    },
  },
  methods: {
    removeTask() {
      this.$emit('removerTask', this.task);
    },
  },
});
</script>

<style scoped>
  .task{
    border-radius: 8px;
    font-size: 1.2rem;
    cursor:  pointer;
    user-select: none;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .pending{
    border-left: 12px solid #b73229;
    background-color: #f44336;
    color: black;
    font-weight: bolder;
  }

  .done{
    color: black;
    border-left: 12px solid #0A8f08;
    background-color: #4caf50;
    text-decoration: line-through;
  }
</style>
