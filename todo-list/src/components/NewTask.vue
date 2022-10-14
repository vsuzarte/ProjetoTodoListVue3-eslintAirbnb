<template>
  <div class="columns is-gapless is-centered">
    <div class="column is-2"></div>
    <div class="column is-6">
      <input
        v-model="nome"
        @keydown.enter="add"
        class="input is-primary"
        aria-label="Adicionar tarefa"
        placeholder="Adicionar tarefa"
        type="text"
      >
    </div>
    <div class="column is-2">
      <button @click="add" class="button is-primary">+</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'NewTask',
  data() {
    return {
      nome: '',
    };
  },
  methods: {
    add() {
      this.$emit('taskAdd', { name: this.nome });
      this.nome = '';
    },
  },
});
</script>

<style scoped>
</style>
