<template>
  <!--
    <h1>{{ msg }}</h1>
  <button @click="count++">count is: {{ count }}</button>
  <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
  -->
  <div class="parc-container">
    <div class="parc" v-for="item in parc">
      <p> {{ item.fields.nom_complet }}</p>
      <p>jardin clos: {{ item.fields.jardin_clos }}</p>
      <p>adresse: {{ item.fields.adresse }} {{ item.fields.code_postal }} {{ item.fields.code_postal }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      count: 0,
      parc: null
    }
  },
  mounted () {
    axios
      .get('https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_parcs-jardins-nantes&q=&rows=28')
      .then(response => (this.parc = response.data.records))
  }
}
</script>
