<template>
  <div>
    <h3>List of products</h3>
    <ul class="list-group">
      <li
        class="list-group-item"
        v-for="product in data_products" :key="product.id"
      >
        <span class="badge badge-primary float-right">{{product.updated_at}}</span>
        <p class="my-0">{{product.name}} - <span class="my-0 font-weight-bold">Bs. {{product.price}}</span></p>
        <small>{{product.description}}</small>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['data_products'],
  methods: {
    
  }
}
</script>

<style>

</style>