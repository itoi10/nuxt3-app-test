<script setup lang="ts">

const hello = ref<string>('Hello! Nuxt 3')

const changeString = (newValue: string) => {
  hello.value = newValue
}

</script>

<template>
  <div>
    <h1>{{ hello }}</h1>
    <button @click="changeString('こんにちは! Nuxt 3')">
      Click!
    </button>
    <NuxtWelcome />
  </div>
</template>
