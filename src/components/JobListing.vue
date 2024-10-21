<script setup>
import { RouterLink } from "vue-router";
import { defineProps, ref, computed } from "vue";

// Define props
const props = defineProps({
  job: Object,
});

// Boolean to toggle full description
const showFullDescription = ref(false);

// Computed property for truncating description
const truncatedDescription = computed(() => {
  const maxLength = 90;
  let description = props.job.description;

  // Truncate only if showFullDescription is false
  if (!showFullDescription.value && description.length > maxLength) {
    description = description.substring(0, maxLength) + "...";
  }
  return description;
});

// Toggle the description
const toggleDescription = () => {
  showFullDescription.value = !showFullDescription.value;
};
</script>

<template>
  <div class="bg-white rounded-xl shadow-md relative">
    <div class="p-4">
      <div class="mb-6">
        <div class="text-gray-600 my-2">{{ job.type }}</div>
        <h3 class="text-xl font-bold">{{ job.title }}</h3>
      </div>

      <!-- Display truncated or full description -->
      <div class="mb-5">
        {{ truncatedDescription }}
      </div>

      <!-- Button to toggle description -->
      <button @click="toggleDescription" class="text-blue-500 underline">
        {{ showFullDescription ? "Show Less" : "Show More" }}
      </button>

      <h3 class="text-green-500 mb-2">{{ job.salary }} / Year</h3>

      <div class="border border-gray-100 mb-5"></div>

      <div class="flex flex-col lg:flex-row justify-between mb-4">
        <div class="text-orange-700 mb-3">
          <i class="pi pi-map-marker text-orange-500"></i>
          {{ job.location }}
        </div>
        <RouterLink
          :to="'/jobs/' + job.id"
          class="h-[36px] bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-center text-sm"
        >
          Read More
        </RouterLink>
      </div>
    </div>
  </div>
</template>
