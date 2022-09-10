<template>
  <BurgerBannerVue/>
  <BurgerForm/>
</template>
<script>
import BurgerBannerVue from '../components/BurgerBanner.vue'
  import BurgerForm from '../components/BurgerForm.vue'
  export default{
    // eslint-disable-next-line vue/multi-word-component-names
    name:'Home',
    components:{
      BurgerForm,
      BurgerBannerVue
    }
  }
</script>
<style>


</style>
