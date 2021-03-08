<template>
  <div>
    <create-product :updateListOfProducts="updateList"/>
    <hr />
    <list-of-products :data_products="products" :deleteProduct="deleteProduct"/>
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
    },
    deleteProduct(index) {
      this.products.splice(index, 1);
    }
  }
}
</script>

<style>

</style>