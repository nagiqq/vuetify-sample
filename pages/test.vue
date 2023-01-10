<template>
  <v-layout>
    <v-navigation-drawer v-model="drawer" :rail="rail" permanent @click="rail = false">
      <v-list-item
        prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
        title="John Leider"
        nav>
        <template v-slot:append>
          <v-btn variant="text" icon="mdi-chevron-left" @click.stop="rail = !rail"></v-btn>
        </template>
      </v-list-item>

      <v-divider></v-divider>

      <v-list density="compact" nav>
        <v-list-item prepend-icon="mdi-minecraft">
          <template v-slot:title>
            <a href="#section1"> How to use Vuetify with Nuxt 3 </a>
          </template>
        </v-list-item>
        <v-list-item prepend-icon="mdi-chart-bubble">
          <template v-slot:title>
            <a href="#section2"> Vuetify 3 官方文件 </a>
          </template>
        </v-list-item>
        <v-list-item prepend-icon="mdi-flask">
          <template v-slot:title>
            <a href="#section3"> How to use Vuetify with Nuxt 3 </a>
          </template>
        </v-list-item>
        <v-list-item prepend-icon="mdi-movie-roll">
          <template v-slot:title>
            <a href="#section4"> ESLint + Prettier 環境建置 </a>
          </template>
        </v-list-item>
        <v-list-item prepend-icon="mdi-routes">
          <template v-slot:title>
            <a href="#section5"> content </a>
          </template>
        </v-list-item>
      </v-list>
      <div class="text-center">
        <v-chip
          v-for="item in filtersList"
          :key="item"
          class="ma-2"
          color="orange"
          text-color="white"
          append-icon="mdi-star">
          {{ item }}
        </v-chip>
      </div>
    </v-navigation-drawer>
    <v-main>
      <ArticleContent1/>
      <v-card id="section1" class="mx-auto" prepend-icon="mdi-minecraft">
        <template v-slot:title>
          <span> nuxt3 官方文件 </span>
        </template>

        <v-card-text>
          <a href="https://nuxt.com/docs/getting-started/introduction">
            https://nuxt.com/docs/getting-started/introduction
          </a>
          <p>
            <v-btn class="my-2" @click="copy(start1)">npx nuxi init "project-name"</v-btn>
          </p>
          <p>
            <v-btn class="my-2" @click="copy(start2)">yarn install</v-btn>
          </p>
        </v-card-text>
      </v-card>
      <v-card id="section2" prepend-icon="mdi-chart-bubble">
        <template v-slot:title>
          <span> Vuetify 3 官方文件 </span>
        </template>

        <v-card-text>
          <a href="https://next.vuetifyjs.com/en/getting-started/installation/">
            https://next.vuetifyjs.com/en/getting-started/installation/
          </a>
        </v-card-text>
      </v-card>
      <v-card id="section3" prepend-icon="mdi-flask">
        <template v-slot:title>
          <span> How to use Vuetify with Nuxt 3 </span>
        </template>

        <v-card-text>
          <ol>
            <li class="pa-2 ma-2">
              <a href="https://codybontecou.com/how-to-use-vuetify-with-nuxt-3.html">
                https://codybontecou.com/how-to-use-vuetify-with-nuxt-3.html
              </a>
            </li>
            <li class="pa-2 ma-2">
              <p>
                <v-btn @click="copy(item.value)">yarn add vuetify@next sass</v-btn>
              </p>
              <br />
              <p>@ /plugins/vuetify.js</p>
              <p>import { createVuetify } from 'vuetify'</p>
              <p>import * as components from 'vuetify/components'</p>
              <p>import * as directives from 'vuetify/directives'</p>

              <p>export default defineNuxtPlugin(nuxtApp => {</p>
              <p>const vuetify = createVuetify({</p>
              <p>components,</p>
              <p>directives,</p>
              <p>})</p>
              <p>nuxtApp.vueApp.use(vuetify)</p>
              <p>})</p>
            </li>
            <li class="pa-2 ma-2">
              <p>config配置</p>
              <br />
              <p>@/ nuxt.config.ts</p>
              <p>import { defineNuxtConfig } from 'nuxt'</p>
              <p>// https://v3.nuxtjs.org/api/configuration/nuxt.config</p>
              <p>export default defineNuxtConfig({</p>
              <p>css: ['vuetify/lib/styles/main.sass'],</p>
              <p>build: {</p>
              <p>transpile: ['vuetify'],</p>
              <p>},</p>
              <p>vite: {</p>
              <p>define: {</p>
              <p>'process.env.DEBUG': false,</p>
              <p>},</p>
              <p>},</p>
              <p>})</p>
            </li>
            <li class="pa-2 ma-2">
              <p>Integrate Vuetify's mdi icons</p>
              <p>
                <v-btn @click="copy(item2.value)">yarn add @mdi/font</v-btn>
              </p>
              <br />
              <p>// nuxt.config.ts</p>
              <p>import {defineNuxtConfig} from 'nuxt'</p>
              <p>export default defineNuxtConfig({</p>
              <p>css: [</p>
              <p>'@mdi/font/css/materialdesignicons.min.css',</p>
              <p>],</p>
              <p>})</p>
            </li>
          </ol>
        </v-card-text>
      </v-card>
      <v-card id="section4" prepend-icon="mdi-movie-roll">
        <template v-slot:title>
          <span> ESLint + Prettier 環境建置 </span>
        </template>

        <v-card-text>
          <ol>
            <li class="pa-2 ma-2">
              <a href="https://ithelp.ithome.com.tw/articles/10294145">
                https://ithelp.ithome.com.tw/articles/10294145
              </a>
              <a href="https://prettier.io/docs/en/options.html">
                prettier官方文件 https://prettier.io/docs/en/options.html
              </a>
            </li>
            <li class="pa-2 ma-2">
              <p>
                <v-btn class="my-2" @click="copy(item3.value)"
                  >yarn add eslint @nuxtjs/eslint-config-typescript eslint-plugin-vue
                </v-btn>
              </p>
              <br />
              <p>.eslintrc.js</p>
              <p>module.exports = {</p>
              <p>env: {</p>
              <p>browser: true,</p>
              <p>es2021: true</p>
              <p>},</p>
              <p>extends: ['@nuxtjs', 'plugin:vue/vue3-recommended', 'prettier'],</p>
              <p>parserOptions: {</p>
              <p>ecmaVersion: 13,</p>
              <p>sourceType: 'module'</p>
              <p>},</p>
              <p>plugins: ['prettier'],</p>
              <p>rules: {</p>
              <p>'no-undef': 'off'</p>
              <p>}</p>
              <p>}</p>
            </li>
            <li class="pa-2 ma-2">
              <p>
                <v-btn @click="copy(item4.value)">
                  yarn add prettier eslint-config-prettier eslint-plugin-prettier
                </v-btn>
              </p>
              <br />
              <p>.prettierrc.js</p>
              <p>module.exports = {</p>
              <p>printWidth: 100, // 每行文字數量達 100 字元就換到新的一行</p>
              <p>semi: false, // 每個語句的結尾不需要分號</p>
              <p>singleQuote: true, // 字串使用單引號，而不是雙引號</p>
              <p>trailingComma: 'none' // 如 Object、Array 內的元素不需要尾隨逗號</p>
              <p>}</p>
            </li>
          </ol>
        </v-card-text>
      </v-card>
      <v-card id="section5" prepend-icon="mdi-routes">
        <template v-slot:title>
          <span> content </span>
        </template>

        <v-card-text>
          <ol>
            <li class="pa-2 ma-2">
              <a href="https://content.nuxtjs.org/get-started">
                https://content.nuxtjs.org/get-started
              </a>
            </li>
            <li class="pa-2 ma-2">
              <p>
                <v-btn class="my-2" @click="copy(item3.value)"
                  >yarn add --dev @nuxt/content
                </v-btn>
              </p>
              <br />
              <p>.eslintrc.js</p>
              <p>module.exports = {</p>
              <p>env: {</p>
              <p>browser: true,</p>
              <p>es2021: true</p>
              <p>},</p>
              <p>extends: ['@nuxtjs', 'plugin:vue/vue3-recommended', 'prettier'],</p>
              <p>parserOptions: {</p>
              <p>ecmaVersion: 13,</p>
              <p>sourceType: 'module'</p>
              <p>},</p>
              <p>plugins: ['prettier'],</p>
              <p>rules: {</p>
              <p>'no-undef': 'off'</p>
              <p>}</p>
              <p>}</p>
            </li>

          </ol>
        </v-card-text>
      </v-card>
      <div class="px-4 py-2 text-center w-100">
        {{ new Date().getFullYear() }} — <strong><a href="/">Vuetify</a></strong>
        <p>
          ps. mid icon -
          <a href="https://pictogrammers.github.io/@mdi/font/2.0.46/"
            >https://pictogrammers.github.io/@mdi/font/2.0.46/</a
          >
        </p>
      </div>
    </v-main>
  </v-layout>
</template>

<script setup>
const rail = ref(true)
const drawer = ref(true)

// 剪貼簿 ↓
// https://vueuse.org/guide/
// npm i @vueuse/core
import { useClipboard } from '@vueuse/core'

const { copy, copied } = useClipboard()

const item = ref('yarn add vuetify@next sass')
const item2 = ref('yarn add @mdi/font')

const item3 = ref('yarn add eslint @nuxtjs/eslint-config-typescript eslint-plugin-vue')
const item4 = ref('yarn add prettier eslint-config-prettier eslint-plugin-prettier')

const start1 = ref('npx nuxi init "project-name"')
const start2 = ref('yarn install')

import { useFiltersStore } from '~/store/filter'

const filtersStore = useFiltersStore()
const filtersList = filtersStore.getData
</script>

<style scoped></style>
