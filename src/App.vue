<script>
import ListTasks from "./components/ListTasks.vue";
export default {
  components: { ListTasks },
  methods: {
    moveTask(origem, destino, task) {
      this.etapas[destino].cards.push(task);
    },
  },
  data: function () {
    return {
      etapas: {
        toDo: {
          name: "toDo",
          titulo: "ToDO",
          cards: [
            { nome: "Refazer tudo", id: "1" },
            { nome: "Refazer component", id: "2" },
          ],
          next: "done",
        },
        done: {
          name: "done",
          titulo: "Done",
          cards: [
            { nome: "Refazer backend", id: "3" },
            { nome: "Corrigir bug component", id: "4" },
          ],
          next: "",
          back: "toDo",
        },
      },
    };
  },
};
</script>

<template>
  <ListTasks :tasks="etapas.toDo" @moveTask="moveTask" />
  <ListTasks :tasks="etapas.done" @moveTask="moveTask" />
</template>

<style></style>
