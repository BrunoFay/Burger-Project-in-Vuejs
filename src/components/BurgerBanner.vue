<template>
  <div class="banner">
    <h1>Make Your Burger</h1>
  </div>
</template>
<script>
  export default {
    name: "BurgerBanner"
  }
</script>
<style>
  .banner{
  background : url('https://images2.alphacoders.com/901/901414.jpg') no-repeat;
  background-size:  cover;
  height: 100vh;
}
.banner h1 {
    color:bisque;
    background-color: rgba(34, 34, 34, 0.801);
    border-radius: 4px;
    width: fit-content;
    padding: 1rem 3rem;
    position: relative;
    top:10rem;
    left: 5rem;
  }
</style>