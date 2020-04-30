<template>
  <div class="body">
    <headernav />
    <!-- carousel start -->
    <div class="carousel-wrapper mb-4">
      <b-carousel
        id="carousel-1"
        v-model="slide"
        :interval="4000"
        fade
        controls
        indicators
        background="#ababab"
        img-width="500"
        img-height="200"
        style="text-shadow: 1px 1px 2px #333;"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
      >
        <!-- Text slides with image -->
        <b-carousel-slide
          caption="Shopping Made Easy"
          text="Best prices you can always trust!"
          img-src="../assets/images/pic30.jpg"
          img-alt="pic1"
        ></b-carousel-slide>

        <!-- Slides with image slot -->
        <b-carousel-slide>
          <template v-slot:img>
            <img
              class="d-block img-fluid w-100"
              src="../assets/images/pic31.jpg"
              alt="pic4"
            />
          </template>
        </b-carousel-slide>

        <!-- Slides with image slot -->
        <b-carousel-slide>
          <template v-slot:img>
            <img
              class="d-block img-fluid w-100"
              src="../assets/images/pic32.jpg"
              alt="pic4"
            />
          </template>
        </b-carousel-slide>

        <!-- Slides with img slot -->
        <b-carousel-slide>
          <template v-slot:img>
            <img
              class="d-block img-fluid w-100"
              src="../assets/images/pic33.jpg"
              alt="pic4"
            />
          </template>
        </b-carousel-slide>

        <b-carousel-slide
          img-src="../assets/images/pic35.jpg"
          img-alt="pic4"
        ></b-carousel-slide>

        <b-carousel-slide
          img-src="../assets/images/pic36.jpg"
          img-alt="pic6"
        ></b-carousel-slide>
      </b-carousel>
    </div>
    <!-- carousel end -->

    <!-- Select category -->
    <div class="merchant-category">
      <select v-model="category" class="form-control">
        <option value class="options">--All Categories--</option>
        <option value="pm" class="options">Product Merchant</option>
        <option value="sm" class="options">Service Merchant</option>
      </select>
    </div>

    <section class="mt-3">
      <!--Service Merchant -->
      <div
        v-show="category == 'pm' || category == ''"
        class="merchant-category"
      >
        <div class="category-top d-flex justify-content-between">
          <h4 class="text-white merchant-header">Product Merchants</h4>
          <div class="dropdown">
            <b-dropdown
              id="dropdown-right"
              text="Sort by Price"
              variant="info"
              class="m-2"
            >
              <b-dropdown-item @click="highestToLowest"
                >Lowest to Highest</b-dropdown-item
              >
              <b-dropdown-item @click="lowestToHighest"
                >Highest to Lowest</b-dropdown-item
              >

              <!-- <b-dropdown-item href="#">Something else here</b-dropdown-item> -->
            </b-dropdown>
          </div>
        </div>
        <div class="row">
          <div
            v-for="(product, index) of products"
            :key="index"
            class="col-6 col-sm-4 mb-3"
          >
            <b-card>
              <!-- v-lazy="require(`../assets/images/${product.image}.jpg`)" -->
              <b-card-img-lazy
                :src="require(`../assets/images/${product.image}.jpg`)"
                :alt="product.image"
              ></b-card-img-lazy>
              <b-card-title>
                <div class="d-flex justify-content-between mt-3">
                  <span>
                    <div class="rating d-none d-lg-block">
                      <span>☆</span>
                      <span>☆</span>
                      <span>☆</span>
                      <span>☆</span>
                      <span>☆</span>
                    </div>
                  </span>
                  <span class="text-danger discount"
                    >- {{ product.discount }} %</span
                  >
                </div>
              </b-card-title>
              <b-card-text class="product-desc">
                Description : Lorem ipsum dolor sit amet consectetur....
              </b-card-text>
              <template v-slot:footer>
                <small class="text-muted price"
                  >&#8358;{{ product.price }}</small
                >
              </template>
            </b-card>
          </div>
        </div>
      </div>

      <!-- Service Merchant -->
      <div
        v-show="category == 'sm' || category == ''"
        class="merchant-category"
      >
        <div class="category-top d-flex justify-content-between">
          <h4 class="text-white merchant-header">Service Merchants</h4>
          <div class="dropdown">
            <b-dropdown
              id="dropdown-right"
              text="Sort by Price"
              variant="info"
              class="m-2"
            >
              <b-dropdown-item @click="highestToLowest"
                >Lowest to Highest</b-dropdown-item
              >
              <b-dropdown-item @click="lowestToHighest"
                >Highest to Lowest</b-dropdown-item
              >
              <!-- <b-dropdown-item href="#">Something else here</b-dropdown-item> -->
            </b-dropdown>
          </div>
        </div>
        <div class="row">
          <div
            v-for="(product, index) in products"
            :key="index"
            class="col-6 col-sm-4 mb-3"
          >
            <b-card>
              <!-- v-lazy="require(`../assets/images/${product.image}.jpg`)" -->
              <b-card-img-lazy
                :src="require(`../assets/images/${product.image}.jpg`)"
                :alt="product.image"
              ></b-card-img-lazy>
              <b-card-title>
                <div class="d-flex justify-content-between mt-3">
                  <span>
                    <div class="rating d-none d-lg-block">
                      <span>☆</span>
                      <span>☆</span>
                      <span>☆</span>
                      <span>☆</span>
                      <span>☆</span>
                    </div>
                  </span>
                  <span class="text-danger discount"
                    >- {{ product.discount }} %</span
                  >
                </div>
              </b-card-title>
              <b-card-text>
                Description : Lorem ipsum dolor sit amet consectetur....
              </b-card-text>
              <template v-slot:footer>
                <small class="text-muted price"
                  >&#8358; {{ product.price }}</small
                >
              </template>
            </b-card>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Headernav from '~/components/header.vue'
import products from '~/assets/product.js'

export default {
  name: 'Home',
  components: {
    Headernav
  },
  data() {
    return {
      slide: 0,
      sliding: null,
      products,
      category: ''
    }
  },
  methods: {
    onSlideStart(slide) {
      this.sliding = true
    },
    onSlideEnd(slide) {
      this.sliding = false
    },
    highestToLowest() {
      const products = this.products
      return products.sort((a, b) => parseInt(a.price) - parseInt(b.price))
    },
    lowestToHighest() {
      const products = this.products
      return products.sort((a, b) => parseInt(b.price) - parseInt(a.price))
    }
  }
}
</script>

<style scoped>
.body {
  background: #1a1454;
  background: url('../assets/images/bg.jpg');
  background-size: contain;
  /* height: 200vh; */
  background-repeat: repeat;
}

.merchant-header {
  font-family: 'Montserrat-Medium' !important;
}

.product-desc,
.options {
  font-family: 'Montserrat-Regular' !important;
}

.discount {
  font-size: 15px;
  background: #fcc38a;
  padding: 5px 5px;
}
.price {
  font-size: 17px;
  font-family: 'Montserrat-Bold' !important;
}

.rating > span:hover:before {
  content: '\2605';
  position: absolute;
}
.rating {
  unicode-bidi: bidi-override;
  direction: rtl;
}
.rating > span {
  display: inline-block;
  position: relative;
  width: 0.7em;
}
.rating > span:hover:before,
.rating > span:hover ~ span:before {
  content: '\2605';
  position: absolute;
}
@media (min-width: 768px) {
  .carousel-wrapper {
    width: 700px;
    margin: 0px auto;
  }
  .merchant-category {
    width: 700px;
    margin: 0px auto;
  }
}
</style>
