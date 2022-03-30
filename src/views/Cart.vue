<template>
<section class="cont">


  <h3>Your Cart</h3>
  <main id="cart">
    <div class="container-fluid" v-if="cart">
      <div class="row">
        <div
          class="col-12 col-sm-8 items"
          v-for="carts of cart"
          :key="carts._id"
        >
          <div class="cartItem row" v-for="data of carts.cart" :key="data._id">
            <div class="col-3 mb-2">
              <img class="w-100" :src="data.img" alt="alt image" />
            </div>
            <div class="col-5 mb-2">
              <h6 class=""></h6>

              <p class="pl-1 mb-0">Item: {{ data.title }}</p>
            </div>
            <div class="col-2">
              <p class="cartItemQuantity p-1 text-center">
                Quantity: {{ data.quantity.quantity }}
              </p>
            </div>
            <div class="col-4">
              <p id="cartItem1Price">PRICE: R{{ data.price }}</p>
            </div>
          </div>
          <button class="btn btn-warning" @click="deleteItem(carts._id)">
            Remove
          </button>
          <hr />
        </div>
        <div class="col-12">
          <h3>total: {{ total }}</h3>
          <div v-if="total > 0">
            <button id="btn-checkout" class="btn btn-primary" @click="checkOut">
              <span>Checkout</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </main>
  </section>
</template>

<script>
export default {
  data() {
    return {
      cart: null,

    };
  },
  methods: {
    checkOut() {

          fetch("https://rjbackendpos.herokuapp.com/cart/", {
            method: "DELETE",
            headers: {
              "Content-type": "application/json; charset=UTF-8",
              Authorization: `Bearer ${localStorage.getItem("jwt")}`,
            },
          })
            .then((response) => response.json())
            .then((json) => {
              alert("Items Purchases");
              location.reload();
            })
            .catch((err) => {
              alert(err);
            });
    },
    deleteItem(id) {
      fetch("https://rjbackendpos.herokuapp.com/cart/single", {
        method: "DELETE",
        body: JSON.stringify({
          id: id,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          location.reload();
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
  mounted() {
    if (!localStorage.getItem("jwt")) {
      alert("Please Create Account First");
      return this.$router.push({ name: "Shop" });
    } else {
      fetch("https://rjbackendpos.herokuapp.com/cart/", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.cart = json;
          console.log(this.cart);
        })
        .catch((err) => {
          alert(err);
        });
      
    }
  },
  computed: {
    total: function () {
      var list = this.cart;
      var sum = 0;
      for (var listProps in list) {
        list[listProps].cart.forEach(function (cart) {
          sum += cart.quantity.quantity * cart.price;
        });
      }
      return sum;
    },
  },
};
</script>

<style scoped>
.cont{
  margin-top: 100px;
}
</style>