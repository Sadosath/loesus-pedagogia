<template>
  <img :src="data?.image" alt="" class="product" />
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { IProduct } from '../types/product.type';

@Options({
  props: {
    data: Object as () => IProduct,
  }
})
export default class Product extends Vue {
  data!: () => IProduct;
}
</script>

<style lang="scss">
.product {
  width: 400px;
  margin: 10px 25px 10px 0px;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  transition: transform 0.4s;

  &:hover {
    transform: scale(1.1);
    transform-origin: center;
    cursor: pointer;
  }
}

/*
  Device = Tablets, Ipads
  Screen = B/w 768px to 1024px
*/
@media (max-width: 1024px) {
  .product {
  width: 180px;
  margin: 10px 25px 10px 0px;
  transition: transform 0.4s;

  &:hover {
    transform: scale(1);
    transform-origin: center;
    cursor: unset;
  }
}
}

/*
  Device = Most of the Smartphones Mobiles (Portrait)
  Screen = B/w 320px to 479px
*/
@media (max-width: 480px) {
  .product {
  width: 150px;
}
}
</style>
