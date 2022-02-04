<template>
  <div class="homepage">
    <NavBar />
    <div class="main-content">
      <div class="main-content-details">
        <img :src="selectedProduct?.image" alt="" class="cover" />
        <div class="text">
          <h1 class="title">{{ selectedProduct?.title }}</h1>
          <h4 class="category">
            In
            <span>{{ selectedProduct?.category }}</span>
          </h4>
          <div class="price-rate">
            <div class="price">
              $
              <span>{{ selectedProduct?.price }}</span>
            </div>
            <div class="rate">
              <span class="stars">{{ selectedProduct?.rating?.rate }} ⭐️</span>
              <span class="votes"
                >{{ selectedProduct?.rating?.count }} votes</span
              >
            </div>
          </div>
          <p class="description">
            {{ selectedProduct?.description }}
          </p>
        </div>
      </div>
      <div class="main-content-list">
        <div v-for="product in products" :key="product.id">
          <Product :data="product"></Product>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import NavBar from './components/NavBar.vue';
import Product from './components/Product.vue';
import axios from 'axios';

@Options({
  components: {
    NavBar,
    Product,
  },
  data() {
    return {
      selectedProduct: {},
      products: [],
    };
  },
  mounted() {
    axios
      .get('https://fakestoreapi.com/products')
      .then((response) => {
        this.products = response.data;
        this.selectedProduct = response.data[0];
      })
      .catch((error) => console.log(error));
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
body {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #ffffff;
  color: #444444;
  margin: auto;
}

.homepage {
  margin: 40px;

  .main-content {
    display: flex;
    flex-direction: column;
    margin-top: 50px;

    &-details {
      display: flex;
      align-items: center;
      margin: 0 30px;

      .cover {
        width: 45%;
        height: 50%;
        border-radius: 20px;
      }

      .text {
        margin-left: 25px;

        * {
          margin: 0;
        }

        .title {
          color: #28272c;
          font-size: 2.7rem;
        }

        .category {
          font-size: 1.5rem;
          margin: 15px 0;

          span {
            color: #5344db;
            text-transform: uppercase;
          }
        }
        .price-rate {
          display: flex;

          .price {
            font-size: 1.8rem;
            background-color: #f5f6ff;
            border-radius: 10px;
            padding: 10px 15px;

            span {
              margin-top: 30px;
              font-size: 2.3rem;
              font-weight: 600;
              color: #5344db;
            }
          }

          .rate {
            margin-left: 25px;
            display: flex;
            flex-direction: column;
            font-size: 1.8rem;

            .votes {
              font-size: 1.5rem;
            }
          }
        }
        .description {
          margin-top: 25px;
          font-size: 1.5rem;
          line-height: 2.3rem;
          letter-spacing: 2px;
          text-align: justify;
          overflow: hidden;
          text-overflow: ellipsis;
        }
      }
    }

    &-list {
      margin: 0 30px;
      margin-top: 50px;
      display: flex;
      flex-direction: row;
      align-items: center;
      flex-wrap: nowrap;
      overflow-x: auto;
      overflow-y: hidden;
      -webkit-overflow-scrolling: touch;

      &::-webkit-scrollbar {
        display: none;
      }

      &:first-child {
        margin-left: 25px;
      }

      &:last-child {
        margin-right: 0;
      }
    }
  }
}

/*
  Device = Tablets, Ipads
  Screen = B/w 768px to 1024px
*/
@media (max-width: 1024px) {
  .homepage {
    margin: 20px;

    .main-content {
      margin-top: 30px;

      &-details {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        margin: 0 20px;

        .cover {
          width: 65%;
        }

        .text {
          margin-left: 0;
          margin-top: 10px;

          .title {
            font-size: 2.2rem;
          }

          .category {
            font-size: 1.1rem;
          }

          .price-rate {
            display: flex;

            .price {
              font-size: 1.4rem;

              span {
                font-size: 1.9rem;
              }
            }

            .rate {
              font-size: 1.6rem;

              .votes {
                font-size: 1.4rem;
              }
            }
          }
          .description {
            font-size: 1.3rem;
            line-height: 2.1rem;
          }
        }
      }
    }
  }
}

/*
  Device = Most of the Smartphones Mobiles (Portrait)
  Screen = B/w 320px to 479px
*/
@media (max-width: 480px) {
  .homepage {
    margin: 10px;

    .main-content {
      &-details {
        margin: 0 10px;
        margin-top: 200px;

        .cover {
          width: 100%;
        }

        .text {
          .title {
            font-size: 1.7rem;
          }

          .category {
            font-size: 0.9rem;
          }

          .price-rate {
            .price {
              font-size: 1rem;

              span {
                font-size: 1rem;
              }
            }

            .rate {
              font-size: 1rem;

              .votes {
                font-size: 0.9rem;
              }
            }
          }
          .description {
            margin-top: 15px;
            font-size: 1rem;
            line-height: 1.5rem;
          }
        }
      }

      &-list {
        position: absolute;
        top: 50px;
      }
    }
  }
}
</style>
