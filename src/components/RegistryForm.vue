<template>

  <form v-on:submit.prevent="submitData" class=element-form>
    <div class="form-group">
      <label for="nombres">Nombres</label>
      <input type="input" class="form-control" id="nombres" placeholder="Ingresar Nombres" v-model="registry.names">
    </div>
    <div class="form-group">
      <label for="apellidos">Apellidos</label>
      <input type="input" class="form-control" id="apellidos" placeholder="Ingresar apellidos" v-model="registry.lastNames">
    </div>
    <div class="form-group">
      <label for="fecha">Fecha Nac</label>
      <input type="date" class="form-control" id="fecha" v-model="registry.birthday">
    </div>

    <button type="submit" class="btn btn-primary">Agregar</button>
  </form> 
</template>

<script>
export default {
  name: 'registry-form',

  data () {
    return {
      registry: []
    }
  },
  methods: {
    submitData: function () {
      this.$emit("regSaved", this.registry)
    } 

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.element-form{
  width: 70%;
  margin: 0 auto;
  margin-top: 10px;
}
</style>
