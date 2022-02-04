<template>
  <nav class="header">
    <span class="logo">Loesus <span>Store</span></span>
    <div class="search-bar">
      <img src="../assets/svgs/search.svg" alt="" class="search-icon" />
      <input type="text" placeholder="Rechercher" />
    </div>
  </nav>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({})
export default class NavBar extends Vue {}
</script>

<style lang="scss">
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;

  .logo {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS',
      sans-serif;
    font-size: 3rem;
    color: #5344db;
    span {
      color: #000000;
    }
  }

  .search-bar {
    display: flex;
    width: 20%;
    align-items: center;
    border: 1px solid #d1d1d1;
    border-radius: 10px;
    padding: 5px 10px;

    .search-icon {
      width: 35px;
      height: 35px;
    }
    input {
      height: 50px;
      border: none;
      outline: 0;
      margin-left: 15px;
      font-size: 1.2rem;
    }
  }
}


</style>
