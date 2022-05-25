<script setup lang="ts">

const runtimeConfig = useRuntimeConfig()

const hello = ref<string>('Hello! Nuxt 3')

const changeString = (newValue: string) => {
  hello.value = newValue
  console.log(runtimeConfig.public.apiKey)
}

</script>

<template>
  <div>
    <h1>{{ hello }}</h1>
    <button @click="changeString('こんにちは! Nuxt 3')">
      Click!
    </button>
  </div>
</template>
