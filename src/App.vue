<template>
  <div id="app">
      <nav class="navbar navbar-expand-lg navbar-light bg-light p-4 mb-4">
          <h6 class="container">Rest Countries API</h6>
      </nav>
    <router-view></router-view>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css?family=Nunito+Sans&display=swap');

html, body {
  font-family: 'Nunito Sans', sans-serif;
}

#app {
  font-family: 'Nunito Sans', sans-serif;
}
nav h6{
  font-weight:bold;
}
@media (min-width: 1200px){
.container {
    max-width: 1232px;
}
}
</style>
