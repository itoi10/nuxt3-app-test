<template>
  <v-app>
    <v-card width="400px" class="mx-auto mt-5">
      <v-card-title>
        <h1 class="display-1">
          ユーザー登録
        </h1>
      </v-card-title>

      <v-card-text>
        <v-form>
          <v-text-field v-model="email" type="email" label="メールアドレス" />
          <v-text-field v-model="password" type="password" label="パスワード" />
          <v-card-actions>
            <v-btn color="primary" @click="signUp">
              ユーザー登録する
            </v-btn>
            <v-btn color="secondary" to="./login">
              ログインページへ
            </v-btn>
          </v-card-actions>
        </v-form>
      </v-card-text>
    </v-card>
  </v-app>
</template>

<script setup lang="ts">

import { getAuth, createUserWithEmailAndPassword } from 'firebase/auth'

// Nuxtインスタンス. Nuxt2のthisの代わり
const nuxtApp = useNuxtApp()

const email = ref('')
const password = ref('')

const signUp = () => {
  const auth = getAuth(nuxtApp.$firebase)
  createUserWithEmailAndPassword(auth, email.value, password.value)
    .then((userCredential) => {
      console.log(userCredential.user)
      alert('create user success!')
      console.log('create user success!')
    })
    .catch((e) => {
      alert(e.message)
      console.error('create user failed', e)
    })
}

</script>

<style scoped>
</style>
