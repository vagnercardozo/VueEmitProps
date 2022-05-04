<script>
export default {
  props: ["tasks"],
};
</script>

<template>
  <div class="etapas">
    <ol>
      <div class="titulo">
        {{ tasks.titulo }}
      </div>
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
  </div>
</template>

<style>
.etapas {
  width: 30%;
  background-color: aquamarine;
  justify-content: space-around;
}
.titulo {
  text-align: center;
  font-weight: bold;
  margin-bottom: 25px;
}
li {
  list-style-type: none;
  width: 90%;
  height: 200px;
  background-color: aliceblue;
  margin-bottom: 10px;
}
</style>
