<template>
  <div class="card element-card">
    <h5 class="card-header element-header">{{ registry.names }} {{ registry.lastNames }}</h5>
    <div class="card-body element-body">
      <div>Fecha Nacimiento: {{  registry.birthday }} </div>  
      <div>Edad: {{  registry.yearsOld }} </div>  
      <div>{{  registry.message }} </div>  
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'registry-card',
  props: ['registry']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.element-card{
  width: 85%;
  margin: 0 auto;
  margin-top: 10px;
}

.element-header  {
  text-align: center;
  color: black;
}
.element-body  {
  color: black;
}
</style>
