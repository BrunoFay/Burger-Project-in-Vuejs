<template>
  <div id="burger-table" v-if="burgers">
    <div>
      <div id="burger-table-heading">
        <div class="order-id">#:</div>
        <div>Client:</div>
        <div>Bread:</div>
        <div>Meat:</div>
        <div>Optionals:</div>
        <div>Actions:</div>
      </div>
    </div>
    <div id="burger-table-rows">
      <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
        <div class="order-number">{{ burger.id }}</div>
        <div>{{ burger.name }}</div>
        <div>{{ burger.bread }}</div>
        <div>{{ burger.meat }}</div>
        <div>
          <ul v-for="(optional, index) in burger.optionals" :key="index">
            <li>{{ optional }}</li>
          </ul>
        </div>
        <div>
          <select name="status" class="status" @change="updateBurger($event, burger.id)">
            <option :value="s.type" v-for="s in status" :key="s.id" :selected="burger.status == s.type">
              {{ s.type }}
            </option>
          </select>
          <button class="delete-btn" @click="deleteBurger(burger.id)">Remove</button>
        </div>
      </div>
    </div>
  </div>
  <div v-else>
    <h2>No orders at the moment!</h2>
  </div>
</template>
<script>
  export default {
    name: "OrdersDashboard",
    data() {
      return {
        burgers: null,
        burger_id: null,
        status: []
      }
    },
    methods: {
      async getOrders() {
        const req = await fetch('http://localhost:3000/burgers')
        const data = await req.json()
        this.burgers = data
        // Resgata os status de pedidos
        this.getStatus()
      },
      async getStatus() {
        const req = await fetch('http://localhost:3000/status')
        const data = await req.json()
        this.status = data
      },
      async deleteBurger(id) {
        const req = await fetch(`http://localhost:3000/burgers/${id}`, {
          method: "DELETE"
        });
         await req.json()
        this.getOrders()
      },
      async updateBurger(event, id) {
        const option = event.target.value;
        const dataJson = JSON.stringify({status: option});
        const req = await fetch(`http://localhost:3000/burgers/${id}`, {
          method: "PATCH",
          headers: { "Content-Type" : "application/json" },
          body: dataJson
        });
        const res = await req.json()
        console.log(res)
      }
    },
    mounted () {
    this.getOrders()
    }
  }
</script>
<style scoped>
  #burger-table {
    max-width: 1200px;
    margin: 0 auto;
  }
  #burger-table-heading,
  #burger-table-rows,
  .burger-table-row {
    display: flex;
    flex-wrap: wrap;
  }
  #burger-table-heading {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
  }
  .burger-table-row {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #CCC;
  }
  #burger-table-heading div,
  .burger-table-row div {
    width: 19%;
  }
  #burger-table-heading .order-id,
  .burger-table-row .order-number {
    width: 5%;
  }
  select {
    padding: 12px 6px;
    margin-right: 12px;
  }
button{
  background: #222;
  color:#fcba03;
  font-weight: 700;
  border: 2px solid #222;
  padding: 8px 10px;
  margin:0 auto;
  transition: ease-in 0.2s;
}
button:hover{
  background: rgb(167, 4, 4);
  color:white;
  border: 2px solid transparent;


}
</style>