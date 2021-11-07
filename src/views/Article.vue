<template>
  <div>
    <nav class="container rounded" aria-label="breadcrumb">
      <ol class="breadcrumb p-3 h4">
        <li class="breadcrumb-item"><router-link to="/news">News</router-link></li>
        <li class="breadcrumb-item active" aria-current="page">{{ article.title }}</li>
      </ol>
    </nav>

    <div class="container">
      <div v-if="this.hasImage" class="top-graphic">
        <img :src="article.image">
      </div>
      <div>
        <h2>{{ article.title }}</h2>
        <p>{{ article.body }}</p>
      </div>
    </div>


  </div>
</template>

<script>
export default {
  name: "Article",
  data() {
    return {
      article: {},
      hasImage: false,
    }
  },
  created() {
    this.article = this.$root.$data.articles.find(article => article.id === parseInt(this.$route.params.id));
    if (this.article.image) {
      this.hasImage = true;
    }
  },
};
</script>

<style scoped>
.top-graphic {
  height: 300px;
  background-size: cover;
  position: relative;
  white-space: nowrap;
}
.top-graphic img {
  object-fit: cover;
  object-position: 0% 30%;
  width: 100%;
  height: inherit;
}


</style>
