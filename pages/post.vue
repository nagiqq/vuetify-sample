<template>
  <v-card>
    <ContentList v-slot="{ list}">
    <v-layout>
      <v-navigation-drawer
          permanent
          location="left"
      >
        <template v-slot:prepend>
          <v-list-item
              lines="two"
              prepend-avatar="https://randomuser.me/api/portraits/women/81.jpg"
              title="Jane Smith"
              subtitle="Logged in"
          ></v-list-item>
        </template>

        <v-divider></v-divider>

        <v-list v-for="article in list" :key="article" density="compact" nav >
          <v-list-item :prepend-icon="article.icon"  ><NuxtLink :to="`#section${article.id}`" class="text-decoration-none text-green-darken-3">{{ article.title}}</NuxtLink></v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-main >
        <v-card v-for="article in list" :key="article" :id="`section${article.id}`" class="mx-auto" :prepend-icon="article.icon">
          <template v-slot:title>
            <span> {{ article.title }} </span>
          </template>

          <v-card-text>
            <a v-for="item in article.link" :href="item.title"  class="text-decoration-none text-green-darken-3">
              {{  item.title }}
            </a>
            <p v-for="item in article.button" :key="item">
              <v-btn class="my-2" @click="copyClip" :title="item.title">{{ item.title }}</v-btn>
            </p>
            <v-alert  v-if="article.description" text class="rounded-xl ml-3 mt-3" color="bg-slate-200">
              <div v-html="article.description" />
            </v-alert>
          </v-card-text>
        </v-card>
      </v-main>
    </v-layout>
    </ContentList>
  </v-card>
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

function onClickOutsideStandard () {
  rail.value = false
  console.log('here')
}
function include () {
  return [document.querySelector('.v-navigation-drawer__content')]
}
</script>

<style scoped></style>
