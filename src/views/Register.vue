<template>
<section class="register animate__animated animate__slideInLeft">
  <div class="container">
    <div class="row no-margin">
      <div class="col-lg-6 col-md-6 col-sm-12">
        <div class="content">
          <h1>Cop the freshest kicks Now and look fire.</h1>
          <p class="par">Unlock the sheeesh and cop yourself some fresh kicks.
          </p>
        </div>
      </div>
    </div>
  </div>  
</section>
      
      <div class="col-sm-5">
        <div class="form-data">

        </div>
        <div class="form-body">
          <div class="row form-row">

          </div>
        </div>
      </div>


<div class="col-lg-6 col-md-6 col-sm-12">
<form @submit.prevent="register" class="form neu-border">
    <h2 class="form-heading">Register</h2>
    <input
      class="form-input neu-border-inset"
      type="text"
      v-model="name"
      placeholder="name"
      required
    />
    <input
      class="form-input neu-border-inset"
      type="email"
      v-model="email"
      placeholder="Email"
      required
    />
    <input
      class="form-input neu-border-inset"
      type="password"
      v-model="password"
      placeholder="Password"
      required
    />
    <button type="submit" class="form-btn neu-border">Sign up</button>
    <!-- <p class="reg">Don't have an Account?<router-link :to="{name :'Register'}"> 
             sign up
          </router-link> </p>
     -->
  </form>
</div>

</template>

<script>
export default {
 data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    register() {
      console.log(this.name, this.email, this.password);
      fetch("https://booking--system-coach-client.herokuapp.com/users", {
        method: "POST",
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("User registered");
          localStorage.setItem("jwt", json.jwt);
          this.$router.push({ name: "Login" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
}
</script>

<style>
.reg{
  color: white;

}
.sign{
  color: white;
}
p {
    font-size: 50px;

}
.par{
  font-size: 20px;
}
.register {
  min-height: 100vh;
  padding-top: 40px;

}
body {
 background-color: black;    
  width: 100%;
  height: 100%;
  /* background-image: url(../assets/landing.jpeg); */
}


 .content {
   margin-top: 25%;
   text-align: center;
   color: #FFF;
 /* padding: 30px; */
 }
.content h1{
  font-weight: 600;
  font-size: 3.5rem;
}
@media screen and (max-width: 967px){

}

form {
  height: 480px;
  max-width: 470px;
  margin: 30px auto;
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
input,
select {
  display: block;
  /* padding: 10px 6px; */
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid rgb(77, 135, 202);
  color: rgb(197, 5, 5);
}
input{
  background: none;
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
.submit {
  /* border: ; */
  color: white;
  border-radius: 20px;
    text-align: center;

}

.error {
  color: #ff0062;
  margin-top: 10px;
  font-size: 0.9em;
  font-weight: bold;
}

.register {
  text-align: center;
}
</style>