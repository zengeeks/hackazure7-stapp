<template>
  <div>
    <h1>Fetch API</h1>
    <p>
      <button @click="fetchData">Fetch Data</button>
    </p>
    <h3>{{ message }}</h3>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  setup() {
    let message = ref('未取得')

    const fetchData = async () => {
      const response = await fetch('/api/probe?name=HackAzure!')
      const data = await response.json();
      message.value = data.title
    }

    return {
      fetchData,
      message,
    }
  },
})
</script>