<template>
<input type="text"  placeholder="search blogs" v-model="searchProducts">

  <label class="price">
        Sort Price:
        <select v-model="price" @change="sortPrice(price)">
            <option value="">All</option>
          <option value="asc">Ascending</option>
          <option value="desc">Descending</option>
        </select>
      </label>
      
<div class="container" v-if="filteredProducts">
<div class="card"   v-for="product in filteredProducts"
        :key="product._id"
        :to="{ name: 'BlogDetails', params: { id: product._id } }"
      >
  <img :src="product.img" class="card-img-top" alt="Fissure in Sandstone"/>
  <div class="card-body">
    <h5 class="card-title">{{product.title}}</h5>
    <h5 class="card-title">{{product.price}}</h5>

    <button @click="addToCart(product._id)">Add to cart</button>

  </div>
</div>
</div>
</template>

<script>
export default {

    props:["post","idx"],
 data() {
    return {
      products: [],
      searchProducts: "",
    };
    
},
mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("https://rjbackendpos.herokuapp.com/products", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.products = json;
          this.filteredProducts = json;
          this.products.forEach(async (blog) => {
          
          });
        })
        .catch((err) => {
          alert("User not logged in");
        });
    } else {
      alert("User not logged in");
      this.$router.push({ name: "Login" });
    }
  },
  computed: {
    filteredProducts() {
      return this.products.filter((product) => {
        return product.title.toLowerCase().match(this.searchProducts.toLowerCase())
      })
    }
  },
methods:{
  checkOut(){
    fetch("https:///rjbackendpos.herokuapp.com/cart/", {
            method: "DELETE",
            headers: {
              "Content-type": "application/json; charset=UTF-8",
              Authorization: `Bearer ${localStorage.getItem("jwt")}`,
            },
          })
            .then((response) => response.json())
            .then((json) => {
              alert("Items Purchased!");
              location.reload();
            })
            .catch((err) => {
              alert(err);
            });
  },
  addToCart(id) {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      } else {
        let cart = 1;
        fetch(`https://rjbackendpos.herokuapp.com/cart/${id}/`, {
          method: "POST",
          body: JSON.stringify({
            quantity: cart,
          }),
          headers: {
            "Content-type": "application/json; charset=UTF-8",
            Authorization: `Bearer ${localStorage.getItem("jwt")}`,
          },
        })
          .then((response) => response.json())
          .then((json) => {
            alert("Added to Cart");
            location.reload();
                    return this.$router.push({ name: "cart" });

          })
          .catch((err) => {
            alert(err);
          });
      }
    },
    sortPrice(dir) {
      this.filteredProducts = this.filteredProducts.sort(
        (a, b) => a.price- b.price
      );
      if (dir == "desc") this.filteredProducts.reverse();
    },

}
,
};

</script>

<style>
.container{
  padding-top: 100px;
}
.card{
  width: 30%;
   display: flex;
  display: inline-block;
  margin: 10px;
 
}
.price{
  margin-top: 6rem;
}

</style>