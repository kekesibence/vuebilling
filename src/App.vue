<template>
  <div id="app">
    <table id="table">
      <tr>
        <th>Title</th>
        <th>Price</th>
        <th>Quantity</th>
        <th>Delete/Edit</th>
      </tr>
      <tr v-for="row in rows" v-bind:key="row">
        <td>{{row.title}}</td>
        <td>{{row.price}}</td>
        <td>{{row.quantity}}</td>
        <td><button v-on:click="deleteRow(row.title)">X</button><button>Edit</button></td>
      </tr>
      <tr>
        <td><input type="text" name="title"  placeholder="Title" v-model="inputTitle"></td>
        <td><input type="number" name="price"  placeholder="Price" v-model="inputPrice"></td>
        <td><input type="number" name="quantity" placeholder="Quantity" v-model="inputQuantity"></td>
        <td v-on:click="add">Add</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'App',
  methods: {
    add() {
      if (this.inputTitle != "" && this.inputPrice != "" && this.inputQuantity != ""){
        var ujSor = {
          title: this.inputTitle,
          price: this.inputPrice,
          quantity: this.inputQuantity
        };
      this.rows.push(ujSor),
      this.inputTitle = "",
      this.inputPrice = "",
      this.inputQuantity =""
      }else{
        alert("nem lehet üresen hagyni a mezőket")
      }
    },
    deleteRow(title){
      for(let row of this.rows) {
        if (row.title == title){
           this.rows.splice(this.rows.indexOf(row), 1); 
        }
      }
    }
  },
  data() {
    return {
      "inputTitle": "",
      "inputPrice": "",
      "inputQuantity": "",
      rows: [
        {
          title: 'Kerék',
          price: 100,
          quantity: 12
        },
        {
          title: 'Teleszkóp',
          price: 1000,
          quantity: 300
        },
        {
          title: 'Kormány',
          price: 230,
          quantity: 5
        },
        {
          title: 'Ajtó',
          price: 45120,
          quantity: 321
        },
      ]
    }
  }
}
</script>

<style>

#app {
font-family: 'Times New Roman'
, Times
, serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
color: white;
margin: 25px auto 0;
width: 80%;
background-color: #A36846;
font-size: 14pt;
border: 2mm ridge rgba(125, 83, 62, 0.6);
text-align: left;
}

table{
  width: 100%;
  padding: 1%;
}

th {
  text-align: center;

}
table, th, td {
  border-bottom: 1px solid #7D533E;
  border-right: 1px solid #7D533E;

  padding: 1%;
}
tr:last-child
{
   border-bottom: none;
}
td:last-child
{
   border-right: none;
}
th:last-child
{
   border-right: none;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

body{
  background-color: #EBA46E;
}
</style>

