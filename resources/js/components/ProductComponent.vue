<template>
  <div>
    <create-product :updateListOfProducts="updateList"/>
    <list-of-products :data_products="products"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: []
    }
  },
  created() {
    axios.get('/products')
      .then(res => {
        this.products = res.data;
      });
  },
  methods: {
    updateList(new_product) {
      this.products.push(new_product);
    }
  }
}
</script>

<style>

</style>