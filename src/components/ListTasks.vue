<script>
export default {
  props: ["tasks"],
};
</script>

<template>
  <ol>
    {{
      tasks.titulo
    }}
    <li v-for="task in tasks.cards" :key="task.id">
      {{ task.nome }}
      <input
        v-if="tasks.next"
        type="button"
        value="Proximo"
        @click="$emit('moveTask', tasks.name, tasks.next, task)"
      />
      <input
        v-if="tasks.back"
        type="button"
        value="Anterior"
        @click="$emit('moveTask', tasks.name, tasks.back, task)"
      />
    </li>
  </ol>
</template>

<style></style>
