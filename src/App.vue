<template>
  <div id="app">
    <sign-up />
  </div>
</template>

<script>
import SignUp from './components/CreateClient.vue';

export default {
  name: 'App',
  components: {
    SignUp,
  },
};
</script>

<style lang="scss">
*, ::after, ::before {
    box-sizing: border-box;
}
html {
  font-family: "Istok Web", sans-serif;
  font-style: normal;
  font-weight: bold;
  font-size: 18px;
  line-height: 26px;
  color: #414141;
}

h1,
h2,
h3,
h4 {
  margin: 0;
}
h3 {
  font-size: 18px;
}
p {
  margin: 0;
}
body {
  margin: 0;
  background-color: #fffbf0;
}

.container {
  max-width: 1250px;
  margin: 0 auto;
  padding: 0 15px;
}

.header {
  background-color: #007a88;
  text-align: center;
}
.wrapper {
  display: flex;
  justify-content: space-between;
  text-align: center;
  align-items: center;
  margin: 0 auto;
  height: 70px;
  max-width: 1080px;
  color: #ffffff;
}
.logo {
  &__medods {
    font-weight: bold;
    font-size: 28px;
    line-height: 40px;
  }
  &__med {
    position: relative;
    top: -10px;
    font-weight: normal;
    font-size: 20px;
    line-height: 29px;
  }
}
.newClient {
  font-weight: bold;
  font-size: 28px;
  line-height: 40px;
}
#app {
  font-family: Istok Web, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 65px;
}

@media (max-width: 1145px) {
  .wrapper {
    padding: 0 15px;
  }
}
@media (max-width: 460px) {
  .wrapper {
    padding: 0 ;
  }
  .newClient{
    margin-left: 15px;
    font-size: 20px;
    line-height: 20px;
  }
}
</style>
