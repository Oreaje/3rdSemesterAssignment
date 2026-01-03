<script setup lang="ts">
import { computed } from 'vue'
import { marked } from 'marked'
import DOMPurify from 'dompurify'

// Props from parent
const props = defineProps<{ content: string }>()

// Computed HTML for preview
const renderedHtml = computed(() => {
  // Tell TypeScript this is definitely a string
  const html: string = marked.parse(props.content || '') as string

  // Sanitize HTML
  return DOMPurify.sanitize(html) as string
})
</script>

<template>
  <div class="flex-1 flex flex-col bg-gray-800 rounded-xl shadow-lg overflow-hidden">
    <h2 class="text-xl md:text-2xl font-bold mb-2 p-4 uppercase text-amber-400 tracking-wide">
      Preview
    </h2>

    <div
      class="flex-1 p-4 overflow-auto prose prose-invert break-words scrollbar-thin scrollbar-thumb-gray-700 scrollbar-track-gray-900"
      v-html="renderedHtml"
    />
  </div>
</template>




<!-- <script setup lang="ts">
import { computed } from 'vue'
import { marked } from 'marked'
import DOMPurify from 'dompurify'

const props = defineProps<{ content: string }>()

const renderedHtml = computed(async () => {
  // Ensure the output of marked is a string
  const html: string = await marked.parse(props.content || '')

  // DOMPurify.sanitize might return string | SafeString, so cast to string
  return DOMPurify.sanitize(html) as string
})
</script>

<template>
  <div class="flex-1 flex flex-col bg-gray-800 rounded-xl shadow-lg overflow-hidden">
    <h2 class="text-xl md:text-2xl font-bold mb-2 p-4 uppercase text-amber-400 tracking-wide">
      Preview
    </h2>

    <div
      class="flex-1 p-4 overflow-auto prose prose-invert break-words scrollbar-thin scrollbar-thumb-gray-700 scrollbar-track-gray-900"
      v-html="renderedHtml"
    ></div>
  </div>
</template> -->
