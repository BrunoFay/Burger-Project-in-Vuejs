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
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  width: 100vw;
  height: 80vh;
}

</style>
