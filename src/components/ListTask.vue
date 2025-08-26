<template>
  <div>
    <v-text-field
      clearable
      label="Adicione Tarefa"
      @keyup.enter="addTask()"
      v-model="task.title"
    ></v-text-field>

    <v-list
      v-model:selected="settingsSelection"
      lines="three"
      select-strategy="leaf"
    >
      <v-list-subheader>Lista do dia</v-list-subheader>

      <v-list-item v-for="(task, index) in tasks" :key="index" :value="index">
        <template v-slot:prepend="{ isSelected }">
          <v-list-item-action start>
            <v-checkbox-btn :model-value="isSelected"></v-checkbox-btn>
          </v-list-item-action>
        </template>

        <v-list-item-title>{{ task.title }}</v-list-item-title>
        <v-list-item-subtitle>{{ task.description }}</v-list-item-subtitle>

        <template v-slot:append>
          <v-menu>
            <template v-slot:activator="{ props }">
              <v-btn
                color="grey-lighten"
                icon="mdi-dots-vertical"
                variant="text"
                v-bind="props"
              >
              </v-btn>
            </template>
            <v-list>
              <v-list-item>
                <v-list-item-title>Editar</v-list-item-title>
              </v-list-item>
              <v-list-item>
                <v-list-item-title>Deletar</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </template>
      </v-list-item>
    </v-list>
  </div>
</template>
<script setup>
import { ref } from "vue";
const tasks = ref([
  { title: "Estudar Vue", description: "ESTUDAR VUE" },
  { title: "Testar aplicativo", description: "TESTAR COM ATENÇÃO !!" },
]);
const task = ref({
  title: "",
  description: "",
});

const addTask = () => {
  tasks.value.push({
    title: task.value.title,
    description: task.value.description,
  });
  task.value = {
    title: "",
    description: "",
  };
};
</script>
<style scoped>
</style>