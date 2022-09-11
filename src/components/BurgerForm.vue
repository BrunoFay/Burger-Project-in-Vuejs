<template>
<div class="form-container">
  <h1>Choose your burger ingredients</h1>
  <form @submit.prevent="createBurger">
  <div class="input-group">
    <label >
     <span> Client Name</span>
      <input type="text" placeholder="Enter your name" v-model="clientName"/>
    </label>
    <label >
      <span>Choose the bread</span>
      <select name="bread" v-model="bread">
        <option v-for="bread in breads" :key="bread.id" :value="bread.type">
        {{bread.type}}
        </option>
      </select>
    </label>
    <label >
     <span> Choose your hamburger meat</span>
      <select name="meat" v-model="meat">
        <option v-for="meat in meats" :key="meat.id" :value="meat.type">
        {{meat.type}}
        </option>
      </select>
    </label>
    <div class="checkbox-group">
      <span>Select the salads:</span>
      <label v-for="saladsOptional in optionalsData" :key="saladsOptional.id">
        <input type="checkbox" name="optionals" :value="saladsOptional.type" v-model="optionals"/>
      {{saladsOptional.type}}
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
        optionalsData:null,
        status:'requested',
        clientName:'',
        optionals:[],
        bread:null,
        meat:null,
        msg:null
      }
    },
    methods:{
      async getIngredients(){
        const reqIngredients= await fetch('http://localhost:3000/ingredients')
        const response = await reqIngredients.json()
        this.breads= response.breads
        this.meats= response.meats
        this.optionalsData= response.optionals
      },
      async createBurger(){
          const newBurger= {
            name:this.name,
            meat:this.meat,
            bread:this.bread,
            optionals:Array.from(this.optionals),
            status:this.status
          }
          const newBurgerJsonFormat = JSON.stringify(newBurger)
          console.log(newBurgerJsonFormat)
          await fetch('http://localhost:3000/burgers',{
              method: 'POST',
              headers:{"Content-Type": "application/json"},
              body: newBurgerJsonFormat
          })
          this.name=''
          this.meat=''
          this.bread=''
          this.optionals=''
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