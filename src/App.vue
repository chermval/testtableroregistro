<template>
  <div id="app">
    <h2>Tablero de Registros</h2>
     
      <registry-form v-on:regSaved="addRegistry"></registry-form>
      <br>
      <div v-for="registry in registries" v-bind:key="registry.id">
        <registry-card  
          v-bind:registry="registry" >
        </registry-card> 
      </div>
  </div>
</template>

<script>
import RegistryCard from './components/RegistryCard'
import RegistryForm from './components/RegistryForm'
import axios from 'axios'

export default {
  name: 'App',
  data () {
    return {
      registries: []
    }
  },
  components: {
    RegistryCard,
    RegistryForm
  },
  methods: {
    getAllRegistries: function () {
      const baseURI = 'http://localhost:8080/v1/registries'

      axios.get(baseURI).then((response) => {
          console.log(response.data)
          this.registries = response.data
        }, (error) => {
          console.log(error)
        })
    } ,

    addRegistry: function (dataForm) {
      const baseURI = 'http://localhost:8080/v1/registries'

      axios.post(baseURI, {
        names: dataForm.names,
        lastNames: dataForm.lastNames,
        birthday: dataForm.birthday
      }).then((response) => {
        this.getAllRegistries()
        console.log(response.data)
          
      }).catch(e => {
          console.log(e)
      })

    }  

  },
      mounted: function () {
      this.getAllRegistries()
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
