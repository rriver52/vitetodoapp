<script setup>
import useTodos from '../composable/useTodos';

const {pending, completed, changeStatus} = useTodos();

defineProps({
    isCompleted: {
        default: false,
        type: Boolean,
    },
});
</script>


<template>
     <div class="w-1/3">
          <h3 class="text-2xl text-center" :class="isCompleted ? 'text-orange-400' : 'text-red-400'" > {{isCompleted ? "Completed" : "Pending" }}</h3>
          <ul class="pt-8 space-y-4">
            <li
              v-for="todo in isCompleted ? completed : pending"
              :key="todo.id"
              @click="changeStatus(todo.id)"
              :class="isCompleted ? 'text-red-600 hover:bg-yellow-400' : 'text-red-600 hover:bg-red-400' "
              class="w-full px-4 py-2 font-bold text-center text-purple-600 transition-colors duration-500 bg-gray-300 rounded-lg hover:cursor-pointer hover:bg-red-400 hover:text-gray-200"
            >
              {{ todo.text }}
            </li>
          </ul>
        </div>
</template>