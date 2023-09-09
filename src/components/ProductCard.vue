<template>
  <div class="row align-items-start product-card " data-toggle="modal" data-target="exampleModalCenter">
    <div class="col-md-9">
      <div class="food-item-name">
        <h3>{{ product.short_name }}</h3>
        <p class="food-description"></p>
        <div class="food-item-price">
          <p>{{ product.price.currency }}{{ product.price.price }}</p>
        </div>
      </div>
    </div>
    <div class="col-md-3">
      <div class="food-item-image">
        <template v-for="image in product.files" :key="image.id">
          <img :src=" 'https://api-flava.yumaapp.uk/api/products/image/' + image.file_name">
        </template>
        
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    product: Object,
  },
  methods: {
    openModal() {
      this.$emit('open-modal', this.product);
    },
  },
};
</script>
