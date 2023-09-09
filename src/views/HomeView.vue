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
                <CategoryView />
              </div>
              <div class="col-md-8">
                <div data-bs-spy="scroll" data-bs-target="#list-example" data-bs-smooth-scroll="true" class="scrollspy-example" tabindex="0">
                  <template v-for="category in responseData" :key="category.id">
                  <div v-for="item in category.subCategories" :key="item.id" :id="item.key" class="all-list-item-content alllistitem-content-large">
                    <div class="accordion" :id="'accordionExample' + item.key">
                      <div class="accordion-item">
                        <h2 class="accordion-header category-accordion-header">
                          <button class="accordion-button food-item-accordion-button collapsed" type="button" data-bs-toggle="collapse" :data-bs-target="'#sub'+ item.key" aria-expanded="false" :aria-controls="'sub' + item.key">{{ item.name }}</button>
                        </h2>
                        <div :id="'sub'+ item.key" class="accordion-collapse collapse show" :data-bs-parent="'#accordionExample' + item.key" style="">
                          <div class="accordion-body food-item-accordion-body">
                              <div class="" v-for="product in filterProductsByCategory(item.key)" :key="product.id">
                                <ProductCard :product="product" />
                               
                              </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div> 
                </template>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md-4">
            
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import CategoryView from '../components/CategoryView.vue';
import axios from 'axios';
import ProductCard from '../components/ProductCard.vue';

export default {
  components: {
    CategoryView,
    ProductCard,
},
  data() {
    return {
      responseData: null, 
      error: null,
      products: [],
    };
  },
  created() {
    //catergory api
  axios.get('https://api-flava.yumaapp.uk/api/category')
      .then((response) => {
        this.responseData = response.data.map((category) => {
          return {
            id: category.id,
            name: category.name,
            subCategories: category.sub_categories.map((subCategory) => ({
              id: subCategory.id,
              name: subCategory.name,
              key: subCategory.key,
              categoryId: subCategory.key,
            })),
          };
        });
      })
    .catch(error => {
      this.error = error;
    });
    //product api
    axios.get('https://api-flava.yumaapp.uk/api/products')
    .then((response) => {
      this.products = response.data;  
      //console.log(this.products)    
    })
    .catch(error => {
      this.error = error;
    });
  },
  methods: {
  // filter 
  filterProductsByCategory(key) {
    return this.products.filter((product) => product.property.category === key);
  },
  
},
  }
</script>


