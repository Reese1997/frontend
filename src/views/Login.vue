<template>
<section class="login animate__animated animate__slideInLeft">
<form @submit.prevent="handleSubmit">
          <label class="h4 text-dark">Already a Member?</label>
              <h1 class="log">Log in:</h1>
    <br /><br />
    <label>First Name</label>
    <input type="name " required v-model="name">

     <label>Last Name</label>
    <input type="last" required v-model="last">

     <label>Contact</label>
    <input type="contact" required v-model="contact">

    <router-link :to="{ path: '/contact/' }"><button>LOG IN</button></router-link>

    <!-- <p>Don't have an Account?<router-link :to="{name :'Register'}"> 
             sign up
          </router-link> </p> -->
  </form>
</section>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      last: "",
      contact: null,
    };
  },

  methods: {
    handleSubmit() {
      fetch("https://booking--system-coach-client.herokuapp.com/contact", {
        method: "POST",
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          message: this.message,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((res) => res.json())
        .then((data) => (this.contact = data))
        .catch((err) => console.log(err.message));
    },
  },
};
</script>

<style scoped>
.login {
  min-height: 100vh;
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
@media screen and (max-width: 967px){

}

form{
  height: 600px; 
  max-width: 470px;
  margin: 70px auto;
  background: white;
  text-align: left;
  padding: 50px;
  border-radius: 10px;
  border-style: ridge;
  background: rgba(255, 255, 255, 0.15);
  box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.18);
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
  color: white;
}
</style>