<template>
  <div class="calculator__app">
    <h2>Formular comenzi</h2>
    <div class="margin">
      <label for="productList">Lista produse: </label>
      <select class="input" id="productList" v-model="selectedProduct">
        <option :value="product" v-for="product in productList">{{ product }}</option>
    </select>
    <div class="margin">
      <label for="price">Pretul: </label>
      <input type="number" class="input" id="price" v-model="selectedPrice" min="1">
    </div>
    <div class="margin">
      <label for="quantity">Cantitatea: </label>
      <input type="number" class="input" id="quantity" v-model="selectedQuantity" min="1">
    </div>
    </div>
    <div>
      <button class="btn" @click="addProductToCommandsList">Add</button>
      <button class="btn" @click="resetProduct">Reset</button>
    </div>

    <div v-if="commandsList.length > 0">
      <table class="margin">
        <tr>
          <th>Nr</th>
          <th>Numele Produsului</th>
          <th>Pretul unei cantitati</th>
          <th>Numarul de cantitati</th>
          <th>Pretul total</th>
        </tr>
        <tr v-for="(product, index) in commandsList" :key="index">
          <td>{{ index+1 }}</td>
          <td>{{ product.name }}</td>
          <td>{{ product.price }}</td>
          <td>{{ product.quantity }}</td>
          <td>{{ product.price*product.quantity }}</td>
        </tr>
      </table>
    </div>
  </div>
  
</template>

<script>

export default {
  data() {
    return {
      productList: ["Mere", "Pere", "Rosii", "Castraveti", "Portocale"],
      selectedPrice: "",
      selectedQuantity: "",
      commandsList: [],
      selectedProduct: "",
    }
  },
  methods: {
    addProductToCommandsList() {
      const newCommand = {};
      newCommand["name"] = this.selectedProduct;
      newCommand["price"] = this.selectedPrice;
      newCommand["quantity"] = this.selectedQuantity;
      this.commandsList.push(newCommand);
    },
  },
  computed: {
  }
}
</script>

<style scoped>

table{
  border: 1px solid black;
}
td, th {
  border: 1px solid black;
  padding: 10px;
  text-align: center;
}

.calculator__app{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.input {
  border: 1px solid teal;
  padding: 10px 15px;
}

.margin{
  margin-top: 15px;
}

.btn{
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}

</style>
