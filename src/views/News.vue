<template>
  <div>
    <div class="container mt-4">
      <div class="row" data-masonry='{"percentPosition": true }'>

          <div class="col-sm-6 col-lg-4 mb-4" v-for="article in articles" :key="article.id">
            <div class="card">
              <img class="card-img-top" :src="article.image">
              <div class="card-body">
                <h5 class="card-title text-center"><router-link :to="'/news/article/' + article.id" class="stretched-link text-dark text-decoration-none">{{ article.title }}</router-link></h5>
                <p class="card-text">{{ preview(article) }} <router-link :to="'/news/article/' + article.id">(see more)</router-link></p>
                <p class="card-text text-end"><small class="text-muted">Posted {{ article.date }}</small></p>
              </div>
            </div>
          </div>

      </div>
    </div>
  </div>

</template>

<script>
export default {
  name: "News",
  computed: {
    articles() {
      return this.$root.$data.articles
      //Later I may want to add search functions to the news page
      //return this.$root.$data.articles.filter(article => article.name.toLowerCase().search(this.filterText.toLowerCase()) >= 0);
    },
  },
  methods: {
    preview(article) {
      let str = article.body.substr(0, 100);
      let wordIndex = str.lastIndexOf(" ");
      return str.substr(0, wordIndex) + '...'
    },
    daysSincePosted(article) {
      let date = article.date;
      date = date.split("-");
      //let month = date[0];
      //let day = date[1];
      let year = date[2];
      return year
    },
  },
};
</script>
