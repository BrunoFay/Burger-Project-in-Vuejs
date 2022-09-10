<template>
<div class="form-container">
  <h1>Choose your burger ingredients</h1>
  <form>
  <div class="input-group">
    <label >
     <span> Client Name</span>
      <input type="text" placeholder="Enter your name" v-model="clientName"/>
    </label>
    <label >
      <span>Choose the bread</span>
      <select name="bread" v-model="bread">
        <option value="">Pick one bread type</option>
        <option v-for="bread in breads" :key="bread.id" :value="bread.tipo">
        {{bread.tipo}}
        </option>
      </select>
    </label>
    <label >
     <span> Choose your hamburger meat</span>
      <select name="meat" v-model="meat">
        <option value="">Pick one meat type</option>
        <option v-for="meat in meats" :key="meat.id" :value="meat.tipo">
        {{meat.tipo}}
        </option>
      </select>
    </label>
    <div class="checkbox-group">
      <span>Select the salads:</span>
      <label v-for="saladsOptional in saladsOptionals" :key="saladsOptional.id">
        <input type="checkbox" name="saladsOptionals" :value="saladsOptional.tipo" v-model="saladsOptionals"/>
      {{saladsOptional.tipo}}
      </label>
    </div>
    <button type="submit">Mount</button>
  </div>
  </form>
</div>
</template>
<script>
  export default {
    name:'BurgerForm',
    data(){
      return{
        breads:null,
        meats:null,
        saladsOptionals:null,
        status:'requested',
        clientName:'',
        bread:null,
        meat:null,
        msg:null
      }
    },
    methods:{
      async getIngredients(){
        const reqIngredients= await fetch('http://localhost:3000/ingredients')
        const response = await reqIngredients.json()
        this.breads= response.paes
        this.meats= response.carnes
        this.saladsOptionals= response.opcionais
      }
    },
    mounted(){
     this.getIngredients()
    }
  }
</script>
<style scoped>
  .form-container,.input-group{
    display: flex;
    gap: 2rem;
    align-items: center;
    flex-direction: column;
  }
  .form-container{
    padding: 3rem 0;
  }
  .checkbox-group span{
    width: 250px;
  }
  .checkbox-group, .input-group > label{
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  label > span,.checkbox-group span {
    font-weight: bold;
    color:#222;
    padding: 5px 10px;
    border-left :4px solid #EA0001;
  }
  input:not(input[type="checkbox"]),select{
    padding: 5px 10px;
    width:250px;
  }
  input[type="checkbox"]{
    margin: 0  0  0 5rem
  }
  button{
    padding: 8px 15px;
    width: 100px;
    border-radius: 4px;
    outline: none;
    border: 1px solid rgba(128, 128, 128, 0.281);
    color:white;
    background: #EA0001;
    font-weight: 700;
    transition: ease-in 0.1s;
  }
  button:hover,button:focus{
    background: #970101;
    border: 1px solid rgba(128, 128, 128, 0.575);
  }
</style>