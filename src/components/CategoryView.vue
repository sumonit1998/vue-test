<template>
  <div class="list-group menu-list">
    <div class="menu-title">
      <h3>Menu</h3>
    </div>
    <div class="menu-list-all-item">
      <template v-for="category in responseData" :key="category.name">
      <a v-for="item in category.subCategories" :key="item.name" class="list-group-item list-group-item-action menu-list-item" :href="'#' + item.key">
        <span>
          <svg class="svg-inline--fa fa-caret-right" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="caret-right" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 256 512" data-fa-i2svg=""><path fill="currentColor" d="M246.6 278.6c12.5-12.5 12.5-32.8 0-45.3l-128-128c-9.2-9.2-22.9-11.9-34.9-6.9s-19.8 16.6-19.8 29.6l0 256c0 12.9 7.8 24.6 19.8 29.6s25.7 2.2 34.9-6.9l128-128z"></path></svg>
        </span>{{ item.name }}
      </a>
    </template>
    </div>
  </div>
</template>
<script>
import axios from 'axios';
export default {
  name: 'CategoryView',
  data() {
    return {
      responseData: null,
      error: null,
    };
  },
  created() {
  axios.get('https://api-flava.yumaapp.uk/api/category')
      .then((response) => {
        // Process the response data to create the desired structure
        this.responseData = response.data.map((category) => {
          return {
            id: category.id,
            name: category.name,
            subCategories: category.sub_categories.map((subCategory) => ({
              id: subCategory.id,
              name: subCategory.name,
              key: subCategory.key,
            })),
          };
        });
        //console.log(this.responseData);
      })
    .catch(error => {
      // Handle any errors here
      this.error = error;
    });
  },
  
}
</script>