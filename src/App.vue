<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/signup"">Signup</router-link> |
      <router-link to="/login"">Login</router-link> |
      <router-link to="/logout"">Logout</router-link> |
    </div>

    <div class="container-fluid">
      <div class="jumbotron">
        <p class="page-header">ACTUM</p>
        <h1>Test Your Skills. Build Your App.</h1>
        <div class="page-header">
        </div>
      </div>
    </div>

    <router-view/>
  </div>

</template>

<style>



body {
  background-image: url("/oriental-tiles.png");
}

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
  color: #ffffff;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.jumbotron {
  background-color: #f4511e; /* Orange */
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 200px;
  color: #ffffff;
}
</style>
