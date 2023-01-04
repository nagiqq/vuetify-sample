<template>
  <div>
    <v-toolbar
        dark
        prominent
        image="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Vuetify使用指南</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-export</v-icon>
      </v-btn>
    </v-toolbar>
    <v-container class="">
      <v-row justify="center">
        <v-col cols="9">
          <v-sheet class="pa-2 ma-2">
            <v-expansion-panels>
              <v-expansion-panel
              >
                <v-expansion-panel-title>
                   <span
                   >
&#127888; nuxt3 官方文件
                   </span>
                </v-expansion-panel-title>
                <v-expansion-panel-text>
                  <a href="https://nuxt.com/docs/getting-started/introduction">
                    https://nuxt.com/docs/getting-started/introduction
                  </a>
                  <p><v-btn class="my-2" @click="copy(start1)">npx nuxi init "project-name"</v-btn></p>
                  <p><v-btn class="my-2" @click="copy(start2)">yarn install</v-btn></p>
                </v-expansion-panel-text>
              </v-expansion-panel>
            </v-expansion-panels>
            <v-expansion-panels>
              <v-expansion-panel
              >
                <v-expansion-panel-title>
                   <span
                   >
&#127754; Vuetify 3 官方文件
                   </span>
                </v-expansion-panel-title>
                <v-expansion-panel-text>
                  <a href="https://next.vuetifyjs.com/en/getting-started/installation/">
                    https://next.vuetifyjs.com/en/getting-started/installation/
                  </a>
                </v-expansion-panel-text>
              </v-expansion-panel>
            </v-expansion-panels>
            <v-expansion-panels>
              <v-expansion-panel
              >
                <v-expansion-panel-title>
                   <span
                   >
  &#9978;  How to use Vuetify with Nuxt 3
                   </span>
                </v-expansion-panel-title>
                <v-expansion-panel-text>
                  <ol>
                    <li class="pa-2 ma-2">
                      <a href="https://codybontecou.com/how-to-use-vuetify-with-nuxt-3.html">
                       https://codybontecou.com/how-to-use-vuetify-with-nuxt-3.html
                      </a>
                    </li>
                    <li  class="pa-2 ma-2">
                      <p> <v-btn
                          color="red-darken-2" @click="copy(item.value)">yarn add vuetify@next sass</v-btn></p>
                      <br>
                      <p>@ /plugins/vuetify.js</p>
                      <p> import { createVuetify } from 'vuetify'</p>
                      <p> import * as components from 'vuetify/components'</p>
                      <p> import * as directives from 'vuetify/directives'</p>

                      <p> export default defineNuxtPlugin(nuxtApp => { </p>
                      <p> const vuetify = createVuetify({ </p>
                      <p> components,</p>
                      <p> directives,</p>
                      <p> })</p>
                      <p> nuxtApp.vueApp.use(vuetify)</p>
                      <p> })</p>

                    </li>
                    <li  class="pa-2 ma-2">
                      <p>config配置</p>
                      <br>
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
                      <p><v-btn
                          color="red-darken-2" @click="copy(item2.value)">yarn add @mdi/font</v-btn></p>
                      <br>
                      <p>// nuxt.config.ts</p>
                      <p>import {defineNuxtConfig} from 'nuxt'</p>
                      <p>export default defineNuxtConfig({</p>
                      <p>css: [</p>
                      <p>'@mdi/font/css/materialdesignicons.min.css',</p>
                      <p>],</p>
                      <p>})</p>
                    </li>
                  </ol>

                </v-expansion-panel-text>
              </v-expansion-panel>
            </v-expansion-panels>

          </v-sheet>
        </v-col>
      </v-row>
    </v-container>

    <div class="px-4 py-2 text-center w-100">
      {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      <p> ps. html icon - <a href="https://www.w3schools.com/charsets/ref_emoji.asp">https://www.w3schools.com/charsets/ref_emoji.asp</a></p>
    </div>
  </div>
</template>

<script setup>
// 剪貼簿 ↓
// https://vueuse.org/guide/
// npm i @vueuse/core
import { useClipboard } from '@vueuse/core'
const { copy, copied } = useClipboard()

const item = ref('yarn add vuetify@next sass')
const item2 = ref('yarn add @mdi/font')

const start1 = ref('npx nuxi init "project-name"')
const start2 = ref('yarn install')
</script>

<style scoped>

</style>