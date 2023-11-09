<script setup>
import { ref } from 'vue';

import Form from './components/Form.vue';
import List from './components/List.vue';

const itemsList = ref([])

function addTask(input) {
  if (input != "" && itemsList.value.indexOf(input) == -1) {
    itemsList.value.push(input)
  }
}

function removeTask(item) {
  if (itemsList.value.indexOf(item) > -1) {
    itemsList.value = itemsList.value.filter((i) => i != item)
  }
}

</script>

<template>
  <div class="wrapper">
    <h1 class="main-title">Todo App</h1>
    <Form @add-task="addTask"></Form>
    <List :itemsList="itemsList" @remove-task="removeTask"></List>
  </div>
</template>

<style scoped>
  .wrapper {
    max-width: 600px;
    margin: 0 auto;
    padding: 0 15px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .main-title {
    font-size: 28px;
    line-height: 2;
    font-weight: 700;
  }
</style>
