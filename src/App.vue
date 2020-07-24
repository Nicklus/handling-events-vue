<template>
  <div id="app">
    <img
      width="25%"
      src="./assets/logo.png"
    >
    <handling-event />
    <handling-bus-event />
  </div>
</template>

<script>
import HandlingEvent from '@/components/HandlingEvent';
import HandlingBusEvent from '@/components/HandlingBusEvent';

export default {
  name: 'App',
  components: {
    HandlingEvent,
    HandlingBusEvent
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
