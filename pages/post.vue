<template xmlns="http://www.w3.org/1999/html">
  <ContentList v-slot="{ list }">
    <v-card v-for="article in list" :key="article._path" :prepend-icon="article.icon">
      <template v-slot:title>
        <span> {{ article.title }} </span>
      </template>
      <v-card-text>
        <a
          v-for="item in article.link"
          :key="item"
          class="app-link text-decoration-none primary--text font-weight-medium d-inline-block"
          :href="item.title"
          >{{ item.title }}</a
        >

        <p v-for="item in article.button" :key="item">
          <v-btn class="my-2" @click="copyClip" :title="item.title">{{ item.title }}</v-btn>
        </p>
        <v-alert text class="rounded-xl ml-3 mt-3" color="bg-slate-200">
          <div v-html="article.description" />
        </v-alert>
      </v-card-text>
    </v-card>
  </ContentList>
</template>

<script setup>
// 剪貼簿 ↓
// https://vueuse.org/guide/
// npm i @vueuse/core
import { useClipboard } from '@vueuse/core'

const { copy, copied } = useClipboard()

const source = ref('')

function copyClip(event) {
  console.log(event.target.title)
  source.value = event.target.title
  copy(source.value)
}
</script>

<style scoped></style>
