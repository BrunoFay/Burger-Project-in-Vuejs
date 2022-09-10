<template>
 <header>
    <div class="nav-container">
      <RouterLink to="/">
        <img id="logo" src="https://freesvg.org/img/1548610988.png" alt="burger">
      </RouterLink>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/orders">Orders</RouterLink>
      </nav>
    </div>
  </header>
</template>
<script>
  export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name:"Navbar"
  }
</script>
<style>
#logo{
  width:50px;
  height: 50px;
}
header {
  background: #202020;
}
.nav-container{
  display: flex;
  align-items: center ;
  padding: 1rem 1.5rem;
  justify-content: space-between;
}
.nav-container nav {
  display: flex;
  gap: 1rem;
}
.nav-container a {
  color: #fcba03;
  font-weight: 700;
}
</style>