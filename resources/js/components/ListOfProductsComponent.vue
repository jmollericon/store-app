<template>
  <div>
    <h3>List of products</h3>
    <ul class="list-group">
      <li
        class="list-group-item"
        v-for="(product, index) in data_products" :key="product.id"
      >
        <span
          class="badge badge-primary float-right"
        >{{product.updated_at}}</span>
        <p class="my-0">{{index+1}} - {{product.name}} - <span class="my-0 font-weight-bold">Bs. {{product.price}}</span></p>
        <small>{{product.description}}</small>
        <button class="btn btn-danger btn-sm float-right" @click="delete_product(product, index)">Delete</button>
        <button class="btn btn-warning btn-sm float-right mx-2" @click="edit_product(product, index)">Edit</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['data_products', 'deleteProduct', 'editProduct'],
  methods: {
    delete_product(product, index) {
      axios.delete(`/products/${product.id}`)
      .then(() => {
        this.deleteProduct(index);
      });
    },
    edit_product(product, index) {
      this.editProduct(product, index);
    }
  }
}
</script>

<style>

</style>