<script setup>
import { onMounted, ref } from 'vue';

const itemsList = ref([])

const props = defineProps(["itemsList"])

// onMounted(() => {
//   itemsList.value = props.itemsList
// })

function removeTask(item) {
  props.itemsList = props.itemsList.filter((i) => i != item)
}

</script>

<template>
  <div class="list">
    <h2 class="list-title">ToDo List</h2>
    <ul class="list-list">
      <li class="list-item" v-for="item in props.itemsList">
        <p>{{ item }}</p>
        <button type="button" @click="$emit('remove-task', item)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<style>
li {
  list-style: none;
}

.list {
  width: 100%;
  display: flex;
  flex-direction: column;
}

.list-title {
  margin-bottom: 10px;
  font-size: 22px;
  padding-bottom: 5px;
  border-bottom: 2px solid rgb(68, 65, 61);
}

.list-list {
  padding: 10px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.list-item {
  display: flex;
  align-items: center;
  padding: 10px;
  border-radius: 3px;
  border: 2px solid rgb(68, 65, 61);
  background-color: transparent;
  font-size: 1rem;
  line-height: 1;
  color: #f2f0ed;
}

.list-item p {
  flex-grow: 1;
}

.list button {
  padding: 3px;
  background-color: rgb(28, 32, 90);
  border: 2px solid rgb(32, 37, 98);
  border-radius: 3px;
  cursor: pointer;
  font-size: 0.875rem;
  color: rgb(242, 240, 237);
  font-weight: 700;
}

.list button:hover,
.list button:focus-visible {
  outline: none;
  background-color: rgb(37, 44, 115);
  border: 2px solid rgb(48, 54, 123);
}</style>