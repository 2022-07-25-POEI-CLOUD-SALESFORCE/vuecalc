<template>
  <div class="resultSlot">
    <slot></slot>
  </div>
</template>

<script>
  //le slot est un composant d'affichage dont aucune techno à l'intérieur
  export default {
    name: 'ResultSlot'
  }
</script>

<style scoped>
.resultSlot {
  width: 100%;
  background: black;
  color: lime;
  text-align: right;
  font-size: 2.5em;
}
</style>