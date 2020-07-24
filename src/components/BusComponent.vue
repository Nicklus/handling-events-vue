<template>
  <div>
    <button @click="saySomething">BusComponent say</button>
  </div>
</template>

<script>
// pattern "event bus" : on importe dans le composant qui va émettre un événement
import eventBus from '../modules/eventBus';

export default {
  name: 'BusComponent',
  methods: {
    saySomething() {
      // emet l'événement "say-something" dans l'instance de Vue dédié
      eventBus.$emit('say-something');
    }
  }
};
</script>
