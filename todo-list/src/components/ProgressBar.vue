<template>
  <div class="columns is-multiline is-gapless is-centered">
    <div class="column is-10">
      <h5 class="title is-5 text-center">Percentual de tarefas concluídas: {{progresso}}%</h5>
    </div>
    <div class="column is-10">
      <progress
        :value="progresso"
        class="progress is-large is-primary"
        max="100">{{progresso}}%
      </progress>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'ProgressBar',
  props: {
    progresso: { type: Number, required: true },
  },
});
</script>

<style>
.text-center{
  text-align: center;
  margin-bottom: 2px;
}
</style>
