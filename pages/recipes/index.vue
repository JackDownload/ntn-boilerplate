<template>
  <main v-if="recipePosts" class="main">
    <h1 class="title text-left">recipes</h1>
    <ul v-for="(recipePost, index) in recipePosts" :key="index" class="articles">
      <nuxt-link class="article article--clickable" :to="`recipes/${recipePost.slug}`">
        <h3 class="article-title">{{ recipePost.title }}</h3>
        <div v-if="recipePost.gallery">
          <img v-for="image in recipePost.gallery" class="image" :key="image.id" :src="image" />
        </div>
        <div class="mt-4 mb-2">
          <h2 class="inline py-1 px-2 mr-1 bg-accent text-white font-medium rounded-sm dark:bg-accent">
            {{ recipePost.recipe_type }}
          </h2>
          <p class="inline">{{ recipePost.description }}</p>
        </div>
      </nuxt-link>
    </ul>
  </main>
</template>
<script>
export default {
  computed: {
    recipePosts() {
      return this.$store.state.recipePosts
    },
  },
}
</script>
