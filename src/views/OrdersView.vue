<template>
  <div class="dash-container">
    <h1>Manage orders</h1>
    <OrdersDashboard/>
  </div>
</template>
<script>
  import OrdersDashboard from '../components/OrdersDashboard.vue'
  export default{
    components:{
      OrdersDashboard
    }
  }
</script>
<style>
.dash-container{
  height: 80vh;
}
.dash-container h1 {
  text-align: center;
  margin-top: 2rem;
}
</style>
