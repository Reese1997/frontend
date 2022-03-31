<template>
<input type="text"  placeholder="search blogs" v-model="search">

  <label class="price">
        Sort Price:
        <select v-model="price" @change="sortPrice(price)">
            <option value="">All</option>
          <option value="asc">Ascending</option>
          <option value="desc">Descending</option>
        </select>
      </label>
      
<div class="container">
<div class="card"   v-for="blog of blogs"
        :key="blog._id"
        :to="{ name: 'BlogDetails', params: { id: blog._id } }"
      >
  <img :src="blog.img" class="card-img-top" alt="Fissure in Sandstone"/>
  <div class="card-body">
    <h5 class="card-title">{{blog.title}}</h5>
    <h5 class="card-title">{{blog.price}}</h5>

    <button @click="addToCart(blog._id)">Add to cart</button>

  </div>
</div>
</div>
</template>

<script>
export default {

    props:["post","idx"],
  // components: { Loader },
 data() {
    return {
      blogs:null,
      posts: null,
      filteredProducts: null,
      title: "",
      search: "",
    };
    
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
computed: {
    filteredProducts: function () {
      return this.search.filter((blog) => {
        return blog.title.match(this.search);
      });
    },
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
          this.blogs = json;
          this.filteredProducts = json;
          this.blogs.forEach(async (blog) => {
          
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