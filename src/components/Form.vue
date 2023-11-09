<script setup>
import { ref } from 'vue';

const input = ref("")

const emit = defineEmits(['add-task'])

function addTodo() {
  emit("add-task", input.value)
  input.value = "";
}

</script>

<template>
  <form class="form" action="" @submit.prevent="addTodo">
    <input class="form-input" type="text" name="newTodo" autocomplete="off" id="newTodo" v-model="input">
    <label class="form-label" for="newTodo">New ToDo</label>
    <button class="form-btn" type="submit">Add ToDo</button>
  </form>
</template>

<style>
.form {
  padding: 10px 0;
  width: 100%;
  display: flex;
  flex-direction: column;
  position: relative;
}

.form-label {
  position: absolute;
  top: 0;
  left: 10px;
  align-self: flex-start;
  font-size: 0.875rem;
  display: block;
  padding: 0 3px;
  border-radius: 3px;
  border: 2px solid rgb(68, 65, 61);
  background-color: rgb(22, 25, 27);
}

.form-input:hover+.form-label,
.form-input:focus-visible+.form-label {
  border: 2px solid rgb(89, 86, 82);
}

.form-input {
  margin-bottom: 15px;
  padding: 10px;
  border-radius: 3px;
  border: 2px solid rgb(68, 65, 61);
  background-color: transparent;
  font-size: 1rem;
  line-height: 1.5;
  color: #f2f0ed;
}

.form-input:hover,
.form-input:focus-visible {
  outline: none;
  border: 2px solid rgb(89, 86, 82);
}

.form-btn {
  padding: 12px;
  background-color: rgb(28, 32, 90);
  border: 2px solid rgb(32, 37, 98);
  border-radius: 3px;
  cursor: pointer;
  font-size: 1.125rem;
  color: rgb(242, 240, 237);
  font-weight: 700;
}

.form-btn:hover,
.form-btn:focus-visible {
  outline: none;
  background-color: rgb(37, 44, 115);
  border: 2px solid rgb(48, 54, 123);
}
</style>