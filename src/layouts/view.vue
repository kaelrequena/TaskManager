<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer">
          <v-list>
            <v-list-item
                prepend-avatar="https://github.com/yurimarcon/avatars/blob/main/Colored/ToyFaces_Colored_BG_29.jpg?raw=true"
                subtitle="Todo List"
                title="Kael Rodrigues Requena">
            </v-list-item>
        </v-list>
        <v-divider></v-divider>
        <v-list :lines="false" density="compact" nav>
            <RouterLink
            v-for="(item, i) in items"
            :key="i"
            :to="item.to"
            >
                <v-list-item :value="item" color="primary">
                    <template v-slot:prepend>
                      <v-icon :icon="item.icon"></v-icon>
                    </template>
                    <v-list-item-title :textContent="item.text"></v-list-item-title>
                </v-list-item>

            </RouterLink>
        </v-list>

    </v-navigation-drawer>
    
    <v-app-bar>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-app-bar-title>Lista de Tarefas</v-app-bar-title>
    </v-app-bar>
    
    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script setup>
    import { ref } from 'vue'
    import { RouterLink } from 'vue-router';
      const drawer = ref(null)
      const items = [
        { text: 'My Files', icon: 'mdi-folder', to:"/Home"},
        { text: 'Shared with me', icon: 'mdi-account-multiple', to:"/Config" },
      ]
</script>

<style scoped>
    a{
        text-decoration: none;
        color: #505050;
    }
</style>
