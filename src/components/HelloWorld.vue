<template>
  <div>
    <h1>Ecommerce Cart</h1>
    <div class="shopping-list">
      <div class="cart">
        <ul>
          <h2>Cart Items</h2>
          <li v-for="(cart) in cartArray" :key="cart.id">
            {{cart.name}} | Price {{cart.price}}
            <button
              class="delete"
              @click="deleteFromCart(cart)"
            >X</button>
          </li>
        </ul>
      </div>
      <div class="total_items">
        <h2 class="header" v-if="cartArray.length === 0">No items in Cart</h2>
        <v-else>
          <h3>Total Items | {{cartArray.length}}</h3>
        </v-else>

        <ul id="items">
          <li v-for="(item) in items" :key="item.id">
            <p class="item-name">{{ item.name}}</p>
            <p class="item-details">
              <span>
                <strong>Amount:</strong>
              </span>
              {{item.Amount}} |
              <span>
                <strong>Price:</strong>
              </span>
              {{item.price}}
            </p>
            <button @click="addToCart(item)">Add to Cart</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      cartArray: [],
      items: [
        { id: 1, name: "Rice", Amount: "1kg", price: "50 tk" },
        { id: 2, name: "Wheat", Amount: "1kg", price: "56 tk" },
        {
          id: 3,
          name: "Cornflower",
          Amount: "250g",
          price: "45 tk"
        },
        { id: 4, name: "Mustard Oil", Amount: "1/2 Litr", price: "60 tk" },
        { id: 5, name: "Soyabin Oil", Amount: "1 Litr", price: "100 tk" },
        { id: 6, name: "Ghee", Amount: "1kg", price: "200 tk" }
      ]
    };
  },
  methods: {
    addToCart(newItem) {
      this.cartArray.push(newItem);
    },
    deleteFromCart(item) {
      const index = this.cartArray.indexOf(item);
      this.cartArray.splice(index, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
  padding: 0;
}

.header {
  margin-bottom: 10px;
}
.total_items {
  text-align: center;

  float: float;
  width: 1000px;
  background-color: bisque;
}

ul {
  list-style-type: none;
}

li {
  padding: 10px;
  overflow: auto;
}
.item-name {
  font-size: 40px;
  margin: 10px;
}
.item-details {
  margin-bottom: 20px;
}
.delete {
  background-color: #860e0a;
  padding: 3px 10px;
}
button {
  background-color: #4caf50; /* Green */
  border: none;
  color: white;
  padding: 10px 22px;
  text-align: center;
  display: inline-block;
  font-size: 16px;
}
.cart {
  float: right;
  background-color: #ead7cd;
}

li:hover {
  background: rgb(245, 217, 217);
  cursor: pointer;
}
</style>
