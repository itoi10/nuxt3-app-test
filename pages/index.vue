<script setup lang="ts">

import { getFirestore, collection, addDoc } from 'firebase/firestore'

// Nuxtインスタンス. Nuxt2のthisの代わり
const nuxtApp = useNuxtApp()

// firestoreに追加
const addItem = async (item: string) => {
  try {
    // 接続          pluginで設定したfirebase参照
    const db = getFirestore(nuxtApp.$firebase)
    // 追加
    const docRef = await addDoc(collection(db, 'test'), {
      name: item
    })
    console.log('docRef', docRef)
  } catch (e) {
    console.log('error', e)
  }
}

const hello = ref<string>('Hello! Nuxt 3')

</script>

<template>
  <div>
    <h1>{{ hello }}</h1>

    <button @click="addItem('Test1')">
      Firestoreに追加
    </button>
  </div>
</template>
