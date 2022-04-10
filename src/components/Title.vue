<script setup>
import{ref} from "vue";
import useTodos from "../composable/useTodos";

const{ addTodo } = useTodos();

const newTodo = ref("");
const add = () => {
  if(newTodo.value){
    addTodo(newTodo.value);
    newTodo.value = "";
  }
};

</script>
<template>
<h1
        class="pb-4 tracking-tight text-center text-purple-500 text-8xl font-thick "
      >
        🚀 My Todo App Website
      </h1>
      <input
        @change="add"
        v-model="newTodo"
        type="text"
        class="text-2xl text-center rounded-lg py-7 px-7"
        placeholder="New Todo"
      />
</template>
