<template>
  <div class="app">
    <MyHeader />
    <ResultSlot>{{ resultat }}</ResultSlot>
    <form>
      <p>
        <label>Nombre 1</label>
        <input v-model="n1" :class="{ok: valide1, ko: !valide1}" />
      </p>
      <p>
        <label>Nombre 2</label>
        <input v-model="n2" :class="{ok: valide2, ko: !valide2}" />
      </p>
    </form>
    <MyButton texte="Addition" @operation="addition" />
    <MyButton texte="Soustraction" @operation="soustraction" />
    <MyButton texte="Multiplication" @operation="multiplication" />
    <MyButton texte="Division" @operation="division" />
    <MyFooter />
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import ResultSlot from './components/ResultSlot.vue';
import MyButton from './components/MyButton.vue';
import MyFooter from './components/MyFooter.vue';

export default {
  name: 'App',
  components: {
    MyHeader,
    ResultSlot,
    MyButton,
    MyFooter
  },
  data() {
    return {
      n1: null,
      n2: null,
      valide1: null,
      valide2: null,
      resultat: null
    }
  },
  methods: {
    addition() {
      //parseFloat pour forcer les valeurs numériques, sinon concaténation
      this.resultat = parseFloat(this.n1) + parseFloat(this.n2);
    },
    soustraction() {
      this.resultat = parseFloat(this.n1) - parseFloat(this.n2);
    },
    multiplication() {
      this.resultat = parseFloat(this.n1) * parseFloat(this.n2);
    },
    division() {
      if(this.n2 != 0) {
        this.resultat = parseFloat(this.n1) / parseFloat(this.n2);
      }
      else this.resultat = 'Division par zéro';
    }

  },
  // les watchers permettent de surveiller des input
  watch: {
    n1(val) {
      if(isNaN(val)) this.valide1 = false;
      else this.valide1 = true;
    },
    n2(val) {
      if(isNaN(val)) this.valide2 = false;
      else this.valide2 = true;
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
.app {
    width: 40%;
    margin: 0 auto;
    border: 1px solid silver;
  }
.ok {
  border-color: limegreen;
}
.ko {
  border-color: crimson;
}
label {
  display: block;
  font-size: 1.3em;
}
input {
  width: 100%;
  font-size: 2em;
}
</style>
