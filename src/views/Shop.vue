<template>
  <div>

    <div class="container pt-4">
      <h2>Board and Card Games</h2>
      <hr>
    </div>
    <div class="container d-flex flex-wrap justify-content-center p-2">

      <div class="card m-2" style="width: 15rem;" v-for="product in board_games" :key="product.id">
        <img class="card-img-top square-image" :src="product.image">
        <div class="card-body">
          <h5 class="card-title"><router-link :to="'/shop/product/' + product.id" class="stretched-link text-dark text-decoration-none">{{ product.name }}</router-link></h5>
          <h6 class="price-text">{{ product.price }}</h6>
          <p class="card-text">{{ product.description }}</p>
        </div>
      </div>

    </div>


    <div class="container">
      <h2>Merch</h2>
      <hr>
    </div>

    <div class="container d-flex flex-wrap justify-content-center p-2">

      <div class="card m-2" style="width: 15rem;" v-for="product in merch" :key="product.id">
        <img class="card-img-top square-image" :src="product.image">
        <div class="card-body">
          <h5 class="card-title"><router-link :to="'/shop/product/' + product.id" class="stretched-link text-dark text-decoration-none">{{ product.name }}</router-link></h5>
          <h6 class="price-text">{{ product.price }}</h6>
          <p class="card-text">{{ product.description }}</p>
        </div>
      </div>

    </div>


    <div class="container pt-4">
      <h4>Looking for something specific?</h4>
      <div class="form-floating">
        <input type="text" v-model="filterText" class="form-control" id="filterProducts" placeholder="Search">
        <label for="filterProducts">Filter Product Title</label>
      </div>
    </div>


  </div>
</template>

<script>
export default {
  name: "Shop",
  data() {
    return {
      filterText: '',
    }
  },
  computed: {
    products() {
      return this.$root.$data.products.filter(product => product.name.toLowerCase().search(this.filterText.toLowerCase()) >= 0);
    },
    board_games() {
      return this.products.filter(product => product.type === "Card" || product.type === "Board");
    },
    merch() {
      return this.products.filter(product => product.type === "Merch");
    },
  }
};
</script>
