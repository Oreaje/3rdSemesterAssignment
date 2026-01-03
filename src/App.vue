<script setup lang="ts">
import { ref } from 'vue'
import Editor from './components/Editor.vue'
import Preview from './components/Preview.vue'

// Load README.md as raw text
import readme from './docs/README.md?raw'

const markdown = ref(readme) // Start with README content
</script>

<template>
  <main class="flex flex-col md:flex-row h-screen gap-4 p-2 bg-gray-900">
    <!-- Markdown Editor -->
    <Editor :content="markdown" @updateMarkdown="markdown = $event" />

    <!-- Markdown Preview -->
    <Preview :content="markdown" />
  </main>
</template>
