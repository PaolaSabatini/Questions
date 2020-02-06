<template>
  <div id="app">
    <Header/>
    <Wrapper/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Wrapper from './components/Wrapper.vue';

export default {
  name: 'app',
  components: {
    Header,
    Wrapper,
  },
};
</script>

<style lang="scss">

html {
  width: 100%;
  overflow-x: hidden;
  overflow-y: scroll;
}

body {
  width: 100%;
  overflow-y: visible;
  overflow-x: hidden;
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  position: relative;
}
</style>
