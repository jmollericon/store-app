<template>
  <div>
    <h3>Edit Product</h3>
    <form @submit.prevent="update_product">
      <div class="row">
        <div class="col-md-6 mb-2">
          <input
            type="text"
            class="form-control"
            placeholder="Name"
            v-model="product.name"
            required
          >
        </div>
        <div class="col-md-6 mb-2">
          <input
            type="number"
            class="form-control"
            placeholder="Price"
            v-model="product.price"
            step="0.01"
            min="0"
            required
          >
        </div>
        <div class="col-md-12 mb-2">
          <textarea
            class="form-control"
            placeholder="Description"
            v-model="product.description"
            rows="2"
            required
          ></textarea>
        </div>
        <div class="col-md-6 mb-2">
          <select
            class="form-control"
            v-model="product.product_category_id"
            required
          >
            <option value="1">Food</option>
          </select>
        </div>
        <div class="col-md-6">
          <button type="submit" class="btn btn-success">Update</button>
          <button type="button" class="btn btn-danger" @click="cancel_edition">Cancel</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ['updateListOfProducts', 'data_product', 'cancelEdition'],
  data() {
    console.log('data edit coponente');
    return {
      product: this.data_product,
    }
  },
  mounted() {
    console.log('mounted')
  },
  methods: {
    update_product() {
      const params = {
        name: this.product.name,
        description: this.product.description,
        price: this.product.price,
        product_category_id: this.product.product_category_id
      }
      this.product.name = '';
      this.product.description = '';
      this.product.price = '';
      this.product.product_category_i = '';
      axios.put(`/products/${this.data_product.id}`, params)
        .then(res => {
          this.updateListOfProducts(res.data, 'update');
        })
    },
    cancel_edition() {
      console.log('cancelando')
      this.cancelEdition();
    }
  }
}
</script>

<style>

</style>