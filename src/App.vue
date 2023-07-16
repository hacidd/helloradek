<template>
  <div>
    <!-- <nav>
      <router-link to="/">spacer</router-link>
      <router-link to="/about">about</router-link>
    </nav> -->
    <router-view />
  </div>

</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;800&display=swap');

* {
  box-sizing: border-box;
}
html {
  font-size: 62.5%;
}
body {
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
}
</style>
