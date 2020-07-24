<template>
  <div>
    <h1>Handling Event</h1>
    <div>
      <!-- Capture l'événement "dialog-closed" déclenché par le composant enfant "DialogComponent" -->
      <dialog-component @dialog-closed="dialogClosed" />
    </div>
    <div>
      <button @click="clickHandler">Click Handler !</button>
      <ul>
        <li>target :: {{ eventTarget }}</li>
        <li>timeStamp : {{ eventTimeStamp }}</li>
      </ul>
    </div>
    <div>
      <form @submit.prevent="formHandler">
        <label for="fname">First name:</label><br>
        <input
          type="text"
          id="fname"
          name="fname"
          value="John"
        ><br>
        <label for="lname">Last name:</label><br>
        <input
          type="text"
          id="lname"
          name="lname"
          value="Doe"
        ><br><br>
        <input
          type="submit"
          value="Submit"
        >
      </form>
    </div>
  </div>
</template>

<script>
import DialogComponent from '@/components/DialogComponent';
// pattern "event bus" : on import dans le composant qui va écouter l'événement
import eventBus from '../modules/eventBus';

export default {
  name: 'HandlingEvent',
  components: {
    DialogComponent
  },
  created() {
    // le composant écoute l'événement dans le lifecycle hook "created"
    eventBus.$on('say-something', () => {
      console.log(
        'The component "BusComponent" say something to HandlingEvent'
      );
    });
  },
  data() {
    return {
      eventTarget: '',
      eventTimeStamp: ''
    };
  },
  methods: {
    clickHandler(event) {
      // Voir <https://developer.mozilla.org/en-US/docs/Web/API/Event> pour les infos sur l'objet "event"
      alert('You clicked me ??!!');
      this.eventTarget = event.target;
      this.eventTimeStamp = event.timeStamp;
    },
    // Affectation par décomposition de l'objet passé en paramétre par l'enfant émetteur de l'événement
    dialogClosed({ time }) {
      console.log(`Dialog closed in HandlingEvent at :: ${time}`);
    },
    formHandler(event) {}
  }
};
</script>

