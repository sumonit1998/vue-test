<script setup>
</script>

<template>
  <main class="menu-section">
    <div class="menu-overlay"></div>
    <div class="container">
      <div class="menu-header large-device">
        <div class="row">
          <div class="col-md-12 m-auto">
            <div class="text-center header">
              <h5> You are ordering to Biscot Road 
                <a href="#" class="ms-2 login mt-1 mb-1 btn-sm" style="font-size: 14px;">Change Shop</a>
              </h5>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Product section -->
    <div class="container">
      <div class="position-relative large-device">
        <div class="row">
          <div class="col-md-8">
            <div class="row">
              <div class="col-md-4">
                <div class="list-group menu-list">
                  <div class="menu-title">
                    <h3>Menu</h3>
                  </div>
                  <div class="menu-list-all-item">
                    <template v-for="category in responseData" :key="category.name">
                    <a v-for="item in category.subCategories" :key="item.name" class="list-group-item list-group-item-action menu-list-item" href="">
                      <span>
                        <svg class="svg-inline--fa fa-caret-right" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="caret-right" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 256 512" data-fa-i2svg=""><path fill="currentColor" d="M246.6 278.6c12.5-12.5 12.5-32.8 0-45.3l-128-128c-9.2-9.2-22.9-11.9-34.9-6.9s-19.8 16.6-19.8 29.6l0 256c0 12.9 7.8 24.6 19.8 29.6s25.7 2.2 34.9-6.9l128-128z"></path></svg>
                      </span>{{ item.name }}
                    </a>
                  </template>
                  </div>
                </div>
              </div>
              <div class="col-md-8"></div>
            </div>
          </div>
          <div class="col-md-4"></div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from 'axios';
export default {

  data() {
    return {
      responseData: null, // Initialize as null or an empty array, depending on your data structure
      error: null, // Initialize as null to handle errors
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
            })),
          };
        });
        console.log(this.responseData);
      })
    .catch(error => {
      // Handle any errors here
      this.error = error;
    });
  },
}
</script>


