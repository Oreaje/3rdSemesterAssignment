<script setup lang="ts">
const props = defineProps<{ content: string }>()
const emit = defineEmits<{ (e: 'updateMarkdown', value: string): void }>()

function handleInput(event: Event) {
  const target = event.target as HTMLTextAreaElement
  emit('updateMarkdown', target.value)
}
</script>

<template>
  <div class="flex-1 flex flex-col bg-gray-800 h-full text-lg uppercase rounded-xl shadow-lg overflow-hidden">
    <h2 class="text-xl md:text-2xl font-bold mb-2 p-4 uppercase text-amber-400 tracking-wide">
      Editor
    </h2>

    <textarea
      class="flex-1 w-full p-4 bg-gray-700 text-gray-100 font-mono text-sm md:text-base resize-none outline-none overflow-auto placeholder-gray-400"
      placeholder="Write markdown here..."
      :value="content"
      @input="handleInput"
    ></textarea>
  </div>
</template>
