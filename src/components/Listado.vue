<template>
  <div class="container">
    <h1>Crea Una Nueva Tarea</h1>
    <!-- ingreso de datos -->
    <div class="input-group mb-3">
      <input type="text" class="form-control boton" placeholder="Ingresa un Nombre..." aria-label="nombre" aria-describedby="button-addon2" v-model="nombre">
      <div class="input-group-append">
        <button class="btn btn-outline-secondary" type="button" @click="mostrarNombre">Agregar</button>
      </div>
    </div>

    <!-- lista de tareas  -->
    <table class="table table-dark mt-5 text-center" v-show="listaNombres.length > 0">
      <thead>
        <tr>
          <th colspan="3" class="text-center">Lista de Personas Agregadas </th>
        </tr>
        <tr>
          <th>#</th>
          <th>Tarea</th>
          <th>Accion</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(nombre,index) in listaNombres" :key="index">
          <td>{{index+1}}</td>
          <td>{{nombre}}</td>
          <td><button type="button" class="btn btn-danger btn-sm" @click="eliminarNombre(index)">Eliminar</button></td>
        </tr>
        <tr>
          <th colspan="3" class="text-center">Nombres Agregados: {{listaNombres.length}}</th>
        </tr>
      </tbody>
    </table>
  </div>
  
</template>

<script>
export default {
  name: 'Listado',
  data() {
        return {
            nombre: '',
            listaNombres: []
        }
    },
    methods: {
        mostrarNombre(){
            if (this.nombre) {
                this.listaNombres.push(this.nombre);
                this.nombre = "";
            } else {
                console.log("no tiene nombre");
            }
        },
        eliminarNombre(index){
            this.listaNombres.splice(index,1);
        }
    },
}
</script>

<!-- CSS -->
<style scoped>
  .boton{
    width: 100px;
  }
</style>
