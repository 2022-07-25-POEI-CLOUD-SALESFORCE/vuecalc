<template>
  <button @click="operation">{{ texte }}</button>
</template>

<script>
  export default {
    name: 'MyButton',
    // les props viennent du parent
    props: {
      texte: String
    },
    methods: {
      operation() {
        //on va émettre un évènement vers le parent qui devra le traiter
        this.$emit('operation');
      }
    }
  }
</script>

<style scoped>
  button {
    width: 100%;
    height: 30px;
    margin-bottom: 5px;
    display: block;
    font-size: 1.2em;
  }
</style>