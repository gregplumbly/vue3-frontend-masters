<script setup lang="ts">
import { ref } from "vue";

const count = ref(0);
const characterList = ref([
  { name: "greg" },
  { name: "henrik" },
  { name: "hugo" },
]);
const isModalOpen = ref(false);

const increment = () => {
  count.value++;
};

const openModal = () => {
  isModalOpen.value = true;
};

const closeModal = (event: MouseEvent) => {
  // Check if the click is outside the modal content
  if (event.target === event.currentTarget) {
    isModalOpen.value = false;
  }
};
</script>

<template>
  <div>
    <h1>Counter</h1>
    <p>{{ count }}</p>
    <hr />
    <button
      @click="increment"
      class="px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-opacity-50"
    >
      Increment
    </button>
    <button
      @click="openModal"
      class="ml-2 px-4 py-2 bg-green-500 text-white rounded hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-opacity-50"
    >
      Open Modal
    </button>
    <ul>
      <li v-for="character in characterList" :key="character.name">
        {{ character.name }}
      </li>
    </ul>

    <p v-if="characterList.length % 2 === 0">There is an even number</p>
    <p v-else>There is an odd number</p>

    <!-- Modal -->
    <div
      v-if="isModalOpen"
      @click="closeModal"
      class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center"
    >
      <div class="bg-white p-6 rounded-lg shadow-lg" @click.stop>
        <h2 class="text-xl font-bold mb-4">Modal Title</h2>
        <p>This is the modal content.</p>
        <button
          @click="closeModal"
          class="mt-4 px-4 py-2 bg-red-500 text-white rounded hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-opacity-50"
        >
          Close Modal
        </button>
      </div>
    </div>
  </div>
</template>
