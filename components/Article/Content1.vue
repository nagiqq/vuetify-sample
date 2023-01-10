<template>
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
</template>

<script>
export default {
  name: "Content1"
}
</script>

<style scoped>

</style>
