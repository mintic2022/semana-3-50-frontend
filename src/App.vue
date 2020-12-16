<template>
  <div id="app">
    <header>
    <img src='https://colombiatic.mintic.gov.co/679/channels-581_logo_footer_mintic.png' alt="banner tic">

    </header>
    <!-- <div id="nav"> -->
      <!-- <router-link to="/">Login</router-link> | -->
      <!-- <router-link to="/home">Home</router-link> | -->
      <!-- <router-link to="/about">About</router-link> | -->
      <!-- <router-link to="/services">Services</router-link>  -->
      
    <!-- </div> -->
    <router-view/>
    <div>
      <br>
      <br>
      
    </div>
      <!-- Footer -->

    
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
