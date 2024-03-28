<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import Greet from "./components/Greet.vue";
</script>

<template>
  <div class="container">
    <h1>Welcome to ClipboardShared!</h1>

    <div class="row">
      <a href="https://github.com/ClipboardShared" target="_blank">
        <img src="/tauri.svg" class="logo tauri" alt="Tauri logo" />
      </a>
    </div>

    <Greet />
    <div>
      <p>{{ clipboardText }}</p>
    </div>
  </div>
  
</template>

<style scoped>
.logo.vite:hover {
  filter: drop-shadow(0 0 2em #747bff);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #249b73);
}
</style>

<script>
import { defineComponent } from 'vue';
import { readText } from '@tauri-apps/api/clipboard';

export default defineComponent({
  data() {
    return {
      clipboardText: ''
    };
  },
  mounted() {
    this.readClipboard();
  },
  methods: {
    async readClipboard() {
      try {
        // 读取剪贴板中的文本
        this.clipboardText = await readText();
      } catch (error) {
        console.error('Error:', error);
      }
    }
  }
});
</script>
