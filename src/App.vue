<script setup>
import { RouterLink, RouterView, useRoute } from "vue-router";
import { useTodosStore } from "@/stores/todos.js";
const todosStore = useTodosStore();

const route = useRoute();
</script>

<template>
  <div class="container">
    <header>
      <RouterLink to="/" class="w3-bar-item">Todos</RouterLink>
      <RouterLink to="/new" class="w3-bar-item">New Todo</RouterLink>
    </header>
    <hr />
    <div v-if="route.path === '/'">
      <h3>Settings</h3>
      <input type="checkbox" v-model="todosStore.settings.showFinished" /> Show
      finished |
      <input type="checkbox" v-model="todosStore.settings.showUnfinished" />
      Show pending

      <br />
      Select sorting order:
      <select
        name="sortingPriority"
        v-model="todosStore.settings.sortingPriority"
      >
        <option value="default">Show unsorted</option>
        <option value="high">Show high priority first</option>
        <option value="low">Show low priority first</option>
      </select>
    </div>

    <hr />
    <RouterView />
  </div>
</template>

<style></style>
