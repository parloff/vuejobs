<script setup>
// import { defineProps } from "vue";

// Correct usage of defineProps
const props = defineProps({
  bg: {
    type: String,
    default: "bg-gray-100",
  },
});
</script>

<template>
  <div :class="`${props.bg} p-6 rounded-lg shadow-md`">
    <slot></slot>
  </div>
</template>

<!-- <script setup>
import { defineProps } from "vue";

defineProps{{
    bg: {
        type: String,
        default: 'bg-gray-100',
    }
}};
</script>

<template>
  <div :class="`${bg} p-6 rounded-lg shadow-md`">
    <slot></slot>
  </div>
</template> -->
