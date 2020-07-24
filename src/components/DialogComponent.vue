<template>
  <div>
    <button @click="onClose">Click onClose !</button>
  </div>
</template>

<script>
export default {
  name: 'DialogComponent',
  methods: {
    onClose() {
      console.log('close in DialogComponent');
      // Emet l'événement "dialog-closed" au parent et envoie un objet contenant une proprité time
      this.$emit('dialog-closed', { time: Date.now() });
    }
  }
};
</script>
