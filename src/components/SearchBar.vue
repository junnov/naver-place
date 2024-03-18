<template>
  <div class="flex items-center justify-between gap-2 w-full">
    <input
      v-model="searchString"
      type="text"
      class="w-full p-2 px-4 border-2 border-gray-300 rounded-lg focus:ring-2 focus:ring-green-400 outline-none focus:border-green-200"
    />
    <button
      type="submit"
      class="shirink-0 text-2xl p-2 bg-green-500 text-white border-2 border-green-500 rounded-lg hover:bg-green-400 hover:border-green-400 transition-all duration-300 ease-in-out"
      @click="$emit('search', searchString)"
    >
      <Icon icon="tabler:zoom" />
    </button>
  </div>
</template>
<script setup lang="ts">
import { Icon } from "@iconify/vue"
defineEmits(["search"])
const searchString = defineModel()
</script>
