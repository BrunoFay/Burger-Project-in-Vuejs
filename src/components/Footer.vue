<template>
<footer>
  <div class="footer-container">
   <span>Thanks for visiting burger world!</span>
  </div>
</footer>
</template>
<script>
  export default {
    name :'CFooter'
  }
</script>

<style>
  footer{
    width: 100vw;
  }
.footer-container{
  background: #202020;
  padding: 2rem 1.5rem;
  font-weight: 800;

  display:flex;
  justify-content: space-evenly;
  align-items: center;
}
.footer-container span{
  color: #fcba03;
}

</style>