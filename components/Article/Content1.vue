<template>
    <div>
      <a href="https://nuxt.com/docs/getting-started/introduction">
        https://nuxt.com/docs/getting-started/introduction
      </a>
      <p>
        <v-btn class="my-2" @click="copy(start1)">npx nuxi init "project-name"</v-btn>
      </p>
      <p>
        <v-btn class="my-2" @click="copy(start2)">yarn install</v-btn>
      </p>
    </div>
</template>

<script>
export default {
  name: "Content1"
}
</script>

<style scoped>

</style>
