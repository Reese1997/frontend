<template>
  <header>
  <nav class="navbar" fixed="top">
    <a href="#"><img class="logo" src="../assets/sheesh.png" alt="truecadence logo"></a>
    
    <ul id="ul-navigation" class="nav-ul" data-visible="false">
      <li class="nav-li animate__animated animate__fadeInLeft">
        <router-link to="/">Home</router-link>
        </li>
      <li class="nav-li animate__animated animate__fadeInLeft">
        <router-link :to="{ name: 'Product'}">Products</router-link>
      </li>
      <!-- <li class="nav-li animate__animated animate__fadeInLeft">
        <router-link to="/services">Services</router-link>
        </li> --> 
      <li class="nav-li animate__animated animate__fadeInLeft">
        <router-link :to="{ name: 'Register'}">Register</router-link>
        </li>
      <li class="nav-li animate__animated animate__fadeInLeft">
        <router-link :to="{ name: 'Login'}">Log in</router-link>
        </li>
      <li class="nav-li animate__animated animate__fadeInLeft">
        <router-link :to="{ name: 'Contact'}">Contact</router-link>
        </li>
    </ul>
    
    <button class="mobile-toggle" aria-controls="ul-navigation" aria-expanded="false">
      <span class="sr-only">Menu</span>
    </button>
  </nav>
</header>

</template>

<script>
export default {
  data() {
    return {
      isActive: false,
    };
  },
  methods: {
    toggleNav() {
      this.isActive = !this.isActive;
    },
    logout() {
      localStorage.clear();
      this.toggleNav;
    },
  },
};

</script>

<style>
* {
  font-family: 'Bebas Neue', cursive;
font-family: 'League Gothic', sans-serif;
font-family: 'Smooch Sans', sans-serif;
  margin: 0;
  padding: 0;
}
.quote {
  text-align: center;
  background-color: #1b1b1d;
 color: #fff;
  min-height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  /* background-image: url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/4273/moon.png); */
  background-repeat: no-repeat;
  background-size: 500px 500px;
  background-position: top right;
}
p { 
  font-size: 3rem;
  text-indent: -1.3rem;
  max-width: 50rem; 
  text-shadow: 0 0 10px rgba(0,0,0,0.3);
}
p { quotes: '\201c' '\201d'; }
p:before { content: open-quote; }
p:after  { content: close-quote; }
@media all and (max-width: 850px) {
  p { 
    font-size: 2rem; 
    margin: 2rem;
    text-shadow: 0 0 10px rgba(0,0,0,0.6);
  }
}
@media all and (max-width: 500px) {
  body {
    background-position-y: -200px;
    background-position-x: center;
  }
}
nav{
  z-index: 100;
  position: absolute;
  float: left;
}
.navbar {
  width: 100%;
  max-width:100%;
  min-height: 10vh;
  position: fixed;
  top: 0;
  background-color: transparent;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.logo {
  max-width: 100%;
  width: 200px;
  height: auto;
}
/* navbar underline */
ul li a + a {
    margin-left: 16px;
}
ul li a::after {
    content: '';
    position: fixed;
    left: 0px;
    bottom: 0px;
    width: 100%;
    height: 4px;
    background-color: #FEFEFE;
    transform-origin: bottom right;
    transition: transform 0.5s ease;
    transform: scaleX(0);
}
ul a:hover::after {
    transform-origin: bottom left;
    transform: scaleX(1);
}
/* end */

.nav-ul {
  width: 50%;
  height: 7vh;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(3px);
}
.nav-li {
  list-style-type: none;
}
.nav-li a {
  position: relative;
  font-size: 17px;
  font-weight: 600;
  color: rgb(197, 5, 5);
  text-decoration: none;
  text-transform: uppercase;
  letter-spacing: 1.5px;
}
.nav-li a::after {
  content: "";
  position: absolute;
  bottom: -1.6vh;
  left: 0;
  height: 1px;
  width: 0%;
  background-color: white;
  transition: 0.3s ease;
}
.nav-li a:hover::after {
  width: 100%;
}
.sr-only {
  position: absolute;
  left: -10000px;
  top: auto;
  width: 1px;
  height: 1px;
  overflow: hidden;
}
.mobile-toggle {
  display: none;
}

/*hero-section*/
.hero-background {
  height: 120vh;
  background-color: black;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center top;
  display: flex;
  align-items: center;
}
.hero-section-wrapper {
  padding-left: 120px;
}
.hero-text {
  color: rgb(197, 5, 5);
  text-decoration: underline;
  text-transform: uppercase;
  font-size: 17px;
  font-weight: 700;
}
.hero-header {
  color: white;
  font-size: 30px;
  line-height: 40px;
}
.hero-button {
  position: relative;
  margin-top: 30px;
  padding: 10px 20px;
  /* border: 2px solid white; */
  color: rgb(197, 5, 5);
  text-transform: uppercase;
  font-size: 17px;
  font-weight: 700;
  background-color: transparent;
  cursor: pointer;
}
.hero-button span {
  position: relative;
  z-index: 5;
}
.hero-button::after {
  content: "";
  position: absolute;
  width: 100%;
  height: 0%;
  left: 0;
  right: 0;
  top: 100%;
  background-color: rgb(197, 5, 5);
  transition: 0.1s linear;

  border-radius: 7000px
}
.hero-button:hover {
  color: black;
}
.hero-button:hover::after {
  top: 0;
  height: 100%;
}
/******responsive*****/
@media (max-width: 800px) {
  .navbar {
    display: block;
  }
  .logo {
    max-width: 100%;
    width: 100px;
    margin: 10px;
  }
  .nav-ul {
    height: 100vh;
    position: fixed;
    width: 60%;
    inset: 0 0 0 40%;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    padding: 50px 0 0 10px;
    transform: translateX(100%);
    transform-origin:100% 0;
    transition: transform 0.3s linear;
  }
  .nav-ul[data-visible="true"] {
    transform: translateX(0%);
  }
  .nav-li {
    padding: 10px 0;
  }
  .nav-li a {
    font-size: 15px;
    letter-spacing: 1px;
  }
  .mobile-toggle {
    z-index: 1000;
    cursor: pointer;
    position: absolute;
    top: 20px;
    right: 30px;
    border: none;
    display: inline-block;
    width: 30px;
    height: 30px;
    background: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHg9IjBweCIgeT0iMHB4Igp3aWR0aD0iMjQiIGhlaWdodD0iMjQiCnZpZXdCb3g9IjAgMCAxNzIgMTcyIgpzdHlsZT0iIGZpbGw6IzAwMDAwMDsiPjxnIGZpbGw9Im5vbmUiIGZpbGwtcnVsZT0ibm9uemVybyIgc3Ryb2tlPSJub25lIiBzdHJva2Utd2lkdGg9IjEiIHN0cm9rZS1saW5lY2FwPSJidXR0IiBzdHJva2UtbGluZWpvaW49Im1pdGVyIiBzdHJva2UtbWl0ZXJsaW1pdD0iMTAiIHN0cm9rZS1kYXNoYXJyYXk9IiIgc3Ryb2tlLWRhc2hvZmZzZXQ9IjAiIGZvbnQtZmFtaWx5PSJub25lIiBmb250LXdlaWdodD0ibm9uZSIgZm9udC1zaXplPSJub25lIiB0ZXh0LWFuY2hvcj0ibm9uZSIgc3R5bGU9Im1peC1ibGVuZC1tb2RlOiBub3JtYWwiPjxwYXRoIGQ9Ik0wLDE3MnYtMTcyaDE3MnYxNzJ6IiBmaWxsPSJub25lIj48L3BhdGg+PGcgZmlsbD0iI2ZmZmZmZiI+PHBhdGggZD0iTTE0LjMzMzMzLDM1LjgzMzMzdjE0LjMzMzMzaDE0My4zMzMzM3YtMTQuMzMzMzN6TTE0LjMzMzMzLDc4LjgzMzMzdjE0LjMzMzMzaDE0My4zMzMzM3YtMTQuMzMzMzN6TTE0LjMzMzMzLDEyMS44MzMzM3YxNC4zMzMzM2gxNDMuMzMzMzN2LTE0LjMzMzMzeiI+PC9wYXRoPjwvZz48L2c+PC9zdmc+")
      50% 50% no-repeat;
    background-size: 100%;
  }
  .mobile-toggle[aria-expanded="true"] {
    display: inline-block;
    width: 30px;
    height: 30px;
    background: url("data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHg9IjBweCIgeT0iMHB4Igp3aWR0aD0iMjQiIGhlaWdodD0iMjQiCnZpZXdCb3g9IjAgMCAxNzIgMTcyIgpzdHlsZT0iIGZpbGw6IzAwMDAwMDsiPjxnIGZpbGw9Im5vbmUiIGZpbGwtcnVsZT0ibm9uemVybyIgc3Ryb2tlPSJub25lIiBzdHJva2Utd2lkdGg9IjEiIHN0cm9rZS1saW5lY2FwPSJidXR0IiBzdHJva2UtbGluZWpvaW49Im1pdGVyIiBzdHJva2UtbWl0ZXJsaW1pdD0iMTAiIHN0cm9rZS1kYXNoYXJyYXk9IiIgc3Ryb2tlLWRhc2hvZmZzZXQ9IjAiIGZvbnQtZmFtaWx5PSJub25lIiBmb250LXdlaWdodD0ibm9uZSIgZm9udC1zaXplPSJub25lIiB0ZXh0LWFuY2hvcj0ibm9uZSIgc3R5bGU9Im1peC1ibGVuZC1tb2RlOiBub3JtYWwiPjxwYXRoIGQ9Ik0wLDE3MnYtMTcyaDE3MnYxNzJ6IiBmaWxsPSJub25lIj48L3BhdGg+PGcgZmlsbD0iI2ZmZmZmZiI+PHBhdGggZD0iTTMzLjczMzcyLDIzLjU5OTYxbC0xMC4xMzQxMSwxMC4xMzQxMWw1Mi4yNjYyOCw1Mi4yNjYyOGwtNTIuMjY2MjgsNTIuMjY2MjhsMTAuMTM0MTEsMTAuMTM0MTFsNTIuMjY2MjgsLTUyLjI2NjI4bDUyLjI2NjI4LDUyLjI2NjI4bDEwLjEzNDExLC0xMC4xMzQxMWwtNTIuMjY2MjgsLTUyLjI2NjI4bDUyLjI2NjI4LC01Mi4yNjYyOGwtMTAuMTM0MTEsLTEwLjEzNDExbC01Mi4yNjYyOCw1Mi4yNjYyOHoiPjwvcGF0aD48L2c+PC9nPjwvc3ZnPg==")
      50% 50% no-repeat;
    background-size: 100%;
  }
  .nav-li a::after {
    bottom: 0;
  }

  /*****hero-section****/
  .hero-background {
    height: 100vh;
  }
  .hero-section-wrapper {
    padding-left: 15px;
  }
  .hero-text {
    font-size: 14px;
    font-weight: 500;
  }
  .hero-header {
    font-size: 25px;
    line-height: 30px;
  }
  .hero-button {
    margin-top: 15px;
    font-size: 14px;
    padding: 5px 10px;
    font-weight: 500;
  }
}

</style>

