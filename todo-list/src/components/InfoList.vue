<template>
  <div class="columns is-multiline is-centered mt-5">
    <div class="column is-12">
      <h3 class="title is-3">Informações</h3>
    </div>
    <div class="column is-12">
    <ul>
      <li><h4 class="title is-4"> - Crie suas tarefas, usando o campo 'Adicionar Tarefa'.</h4></li>
      <li><h4 class="title is-4"> - Clique em cima das tarefas para finalizar.</h4></li>
      <li><h4 class="title is-4"> - Veja o percentual concluído de suas tarefas.</h4></li>
      <li><h4 class="title is-4"> - Use o 'x' para remover a tarefa.</h4></li>
    </ul>
  </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'InfoList',
});
</script>
