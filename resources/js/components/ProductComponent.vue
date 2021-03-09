<template>
  <div>
    <edit-product :updateListOfProducts="updateList" :data_product="product" :cancelEdition="cancelEdition" v-if="modoEditar"/>
    <create-product :updateListOfProducts="updateList" v-else/>
    <hr />
    <list-of-products :data_products="products" :deleteProduct="deleteProduct" :editProduct="editProduct"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [],
      modoEditar: false,
      product: {}
    }
  },
  created() {
    axios.get('/products')
      .then(res => {
        this.products = res.data;
      });
  },
  methods: {
    updateList(new_product, form) {
      if(form == "store") {
        this.products.push(new_product);
      } else {
        axios.get('/products')
          .then(res => {
            this.products = res.data;
          });
      }
    },
    deleteProduct(index) {
      this.products.splice(index, 1);
    },
    editProduct(product) {
      this.modoEditar = true;
      this.product = product;
    },
    cancelEdition() {
      this.modoEditar = false;
    }
  }
}
</script>

<style>

</style>