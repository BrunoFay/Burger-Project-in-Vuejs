<template>
<footer>
  <div class="footer-container">
   <div>
      <a href="">Contact</a>
      <a href="">Location</a>
   </div>
    <a href="">any</a>
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
.footer-container a{
  color: #fcba03;
}
.footer-container > div{
  display:flex;
 flex-direction: column;
 gap:1rem;
}
</style>