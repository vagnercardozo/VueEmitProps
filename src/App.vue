<script>
import ListTasks from "./components/ListTasks.vue";
export default {
  components: { ListTasks },
  methods: {
    moveTask(origem, destino, task) {
      this.etapas[destino].cards.push(task);

      const removeIndex = this.etapas[origem].cards
        .map((task) => task.id)
        .indexOf(task.id, 0);

      this.etapas[origem].cards.splice(removeIndex, 1);
    },
  },
  data: function () {
    return {
      etapas: {
        investigation: {
          name: "investigation",
          titulo: "Investigation",
          cards: [
            { nome: "Refazer tudo", id: "1" },
            { nome: "Refazer component", id: "2" },
          ],
          next: "toDo",
          back: "",
        },
        toDo: {
          name: "toDo",
          titulo: "ToDo",
          cards: [
            { nome: "Refazer tudo", id: "1" },
            { nome: "Refazer component", id: "2" },
          ],
          next: "done",
          back: "investigation",
        },
        done: {
          name: "done",
          titulo: "Done",
          cards: [
            { nome: "Refazer backend", id: "3"  },
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
  <div class="container">
    <ListTasks :tasks="etapas.investigation" @moveTask="moveTask" />
    <ListTasks :tasks="etapas.toDo" @moveTask="moveTask" />
    <ListTasks :tasks="etapas.done" @moveTask="moveTask" />
  </div>
</template>

<style>
.container {
  display: flex;
  justify-content: space-around;
}
</style>
