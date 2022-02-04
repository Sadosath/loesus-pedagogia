<template>
  <img src="../assets/product.jpg" alt="" class="product" />
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import { IProduct } from '../interfaces/product.type';

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
  width: calc(100% / 4.7);
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


</style>
