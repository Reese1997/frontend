<template>
<!-- <section class="login animate__animated animate__slideInLeft">

  <div class="spaceTaker">

  </div>
  <div class="forme">
    <form @submit.prevent="Login">
          <label class="h4 text-dark">Already a Member?</label>
              <h1 class="log">Log in:</h1>
    <br /><br />
    <label>email</label>
    <input type="text " required v-model="email">

     <label>Password</label>
    <input type="password" required v-model="password">

  <button type="submit">LOG IN</button> -->

    <!-- <p>Don't have an Account?<router-link :to="{name :'Register'}"> 
             sign up
          </router-link> </p> -->
  <!-- </form>
  </div>

</section> -->

<div class="container">
  <div class="row">
    <div class="col">
<section class="login animate__animated animate__slideInLeft">

  <div class="spaceTaker">

  </div>
  <div class="form">
    <form @submit.prevent="Login">
          <label class="h4 text-dark">Already a Member?</label>
              <h1 class="log">Log in:</h1>
    <br /><br />
    <label>email</label>
    <input type="text " required v-model="email">

     <label>Password</label>
    <input type="password" required v-model="password">

  <button type="submit">LOG IN</button>

    <!-- <p>Don't have an Account?<router-link :to="{name :'Register'}"> 
             sign up
          </router-link> </p> -->
  </form>
  </div>

</section>    </div>
  </div>
</div>


</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
          };
  },

  methods: {
    Login() {
      fetch("https://rjbackendpos.herokuapp.com/users", {
        method: "PATCH",
        body: JSON.stringify({
          email: this.email,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          
        },
      })
        .then((res) => res.json())
        .then((json) => {
                    localStorage.setItem("jwt", json.jwt)
                    alert("Logged IN")

        })
        .catch((err) => console.log(err.message));
    },
  },
};
</script>

<style scoped>


.login {
  min-height: 100vh;
  color: black;
}
.head {
  text-align: center;
}
body {
  width: 100%;
  height: 100%;
  /* background-image: url(../assets/landing.jpeg); */
}

.form-label {
  margin-top: 15%;
  background-color: #FFF;
}
.form-body {
  padding: 20px;
}
.form-label {
  padding: 10px;
  border-bottom: 1px solid #CCC;
}
.form-label h2 {
  font-size: 22px;
  font-weight: 600
}
.no-margin {
margin: 0px;
}
.form-label {
  margin-bottom: 15px;
}
.form-control{
  background-color: #AAA;
}
.form-control:hover {
box-shadow: none;
border: 3px solid #138496
}
.content {
  margin-top: 15%;
  text-align: center;
  color: #FFF;;
  padding: 30px;
}
.content h1{
  font-weight: 600;
  font-size: 3.5rem;
}
.forme {
  margin-left: 17%;
  
}

form {
  margin: none;
}
@media screen and (max-width: 967px){

}


form{
  height: 434px; 
  width: 500px;
  max-width: 777px;
  max-height: 552px;
  background: white;
  text-align: left;
  padding: 8px;
  border-radius: 10px;
  border-style: ridge;
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.18);
  /* margin: none !important; */
  margin-left: 36%;
}
label {
  color: rgb(58, 55, 55);
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 1 em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
.form-label {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid rgb(77, 135, 202);
  color: rgb(197, 5, 5);
}

.pill {
  display: inline block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 15px;
  letter-spacing: 1px;
  font-weight: bold;
  color: rgb(197, 5, 5);
  cursor: pointer;
}
button {
  background: rgb(197, 5, 5);
  /* border: ; */
  padding: 20px 30px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
.submit {
  text-align: center;
}
.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.9em;
  font-weight: bold;
}
/* 
.mess {
  width: 100%;
} */

.but {
  margin-left: 46%;
  padding: 15px 29px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
h4{
  color: white;
}
.log{
  color: rgb(7, 6, 6);
}
</style>