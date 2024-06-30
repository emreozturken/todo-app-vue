<script setup lang="ts">
const todoArray: Ref<string[]> = ref([]);
const userInput: Ref<string | null> = ref(null);
const error: Ref<string | null> = ref(null);

const createTask = () => {
  if (!userInput.value) return (error.value = "Please enter a task!");
  todoArray.value.push(userInput.value);
};
</script>

<template>
  <form
    @submit.prevent="createTask"
    class="flex justify-center items-center h-screen flex-col"
  >
    <img src="/todo.png" class="h-20 mb-4" alt="Todo Logo" />
    <h1 class="text-3xl mb-6">TODO App</h1>

    <p class="text-rose-500" v-if="error">
      {{ error }}
    </p>

    <input
      type="text"
      class="border rounded-lg p-2"
      v-model="userInput"
      placeholder="Enter a task please! 😊"
    />

    <button
      type="submit"
      class="mt-4 bg-green-500 p-2 border rounded-lg w-32 text-white"
    >
      Add Task
    </button>

    <div class="mt-10">
      <p
        class="font-bold mb-2 border bg-white rounded-lg p-6 w-96"
        v-for="tasks of todoArray"
      >
        {{ tasks }}
      </p>
    </div>
  </form>
</template>
