<template>
<h1>Product</h1>
<div class="card"   v-for="blog of blogs"
        :key="blog._id"
        :to="{ name: 'BlogDetails', params: { id: blog._id } }"
      >>
  <img :src="blog.img" class="card-img-top" alt="Fissure in Sandstone"/>
  <div class="card-body">
    <h5 class="card-title">{{blog.title}}</h5>
    <!-- <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p> -->
    <a href="#!" class="btn btn-primary">Add to cart</a>
  </div>
</div>
</template>

<script>
export default {
data(){
    return{
      blogs:null
    }
    
},
mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("http://localhost:9990/products", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.blogs = json;
          this.blogs.forEach(async (blog) => {
            await fetch(
              "http://localhost:9990/users" + blog.author,
              {
                method: "GET",
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                },
              }
            )
              .then((response) => response.json())
              .then((json) => {
                blog.author_name = json.name;
              });
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
.card{
  width: 50%;
}

</style>