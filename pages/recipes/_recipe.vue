<template>
  <article v-if="recipePost" class="main article">
    <h1 class="article-title">{{ recipePost.title }}</h1>
    <p class="mt-4">{{ recipePost.description }}</p>
    <img class="cover-image" :src="recipePost.cover" />
    <div class="block mt-8 mb-4" v-html="$md.render(recipePost.body)" />
    <div v-if="recipePost.gallery">
      <img v-for="image in recipePost.gallery" class="image" :key="image.id" :src="image" />
    </div>
  </article>
</template>
<script>
export default {
  async asyncData({ params, payload }) {
    if (payload) return { recipePost: payload }
    else
      return {
        recipePost: await require(`~/assets/content/recipes/${params.recipe}.json`),
      }
  },
}
</script>
