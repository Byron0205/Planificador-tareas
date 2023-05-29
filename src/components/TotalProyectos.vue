<template>
    <div class="table-responsive">
      <h2>Proyectos: {{ numeroProyectos }}</h2>
      <table class="table">
        <thead>
          <tr>
            <th>#</th>
            <th>Proyecto</th>
            <th>Tipo</th>
            <th>Urgente</th>
            <th>Completado</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(proyecto, index) in proyectos" :key="index">
            <td>{{ index+1 }}</td>
            <td>{{ proyecto.proyecto }}</td>
            <td>{{ proyecto.tipo }}</td>
            <!-- <td v-show="proyecto.urgente == true" class="success">Si</td>
            <td v-show="proyecto.urgente == false" class="no-success">No</td> -->
            <td @click="cambiarEstado(proyecto,'urgente')" :class=" proyecto.urgente ? 'success' : 'no-success'">{{ proyecto.urgente ? "SI": "NO" }}</td>
            
            <td @click="cambiarEstado(proyecto,'completado')" :class=" proyecto.completado ? 'success' : 'no-success'">{{ proyecto.completado ? "Completo": "Incompleto" }}</td>
          </tr>
        </tbody>
      </table>
      <div class="progreso">
        <button @click="limpiarTareas">Limpiar Tareas</button>
      </div>
    </div>
</template>

<script>
export default {
    props: {
        proyectos: Array,
        numeroProyectos: Number,
        completado: Boolean,
        limpiarTareas: Function,
        cambiarEstado: Function
    }
}
</script>

<style scoped>
    @import url("../assets/formulario.css");
</style>