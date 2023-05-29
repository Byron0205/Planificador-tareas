<template>
    <div class="container">
    <div class="progreso">
      <h1>Formularios</h1>
      <hr/>
    </div>
    
    <div class="progreso">
        <progress-bar :porcentaje="porcentaje"/>
    </div>
    <div>
      

    <form @submit.prevent="registrarProyecto">
      <div>
        <label for="proyecto">Proyecto</label>
        <input v-model.trim="proyecto" id="proyecto" type="text" required>
      </div>
      
      <div>
        <label for="option">Tipo</label>
        <select v-model.trim="tipo" id="option" required>
          <option >Proyecto Vue.js</option>
          <option >Back end con Node.js</option>
          <option >Movil con React Native</option>
        </select>
      </div>
      
      <div>
        <label for="prioridad">Urgente</label>
        <input v-model="urgente" type="checkbox"/>
      </div>
      

      <button type="submit">Guardar</button>
    </form>
    </div>

    <total-proyectos :proyectos="proyectos" :numeroProyectos="numeroProyectos" :completado="completado"/>
  </div>
</template>

<script>
import ProgressBar from './ProgressBar.vue'
import TotalProyectos from './TotalProyectos.vue'
export default {
  components: { ProgressBar, TotalProyectos },
  data: ()=> ({
    proyecto: "",
    tipo: "",
    urgente: false,
    proyectos: [],
    completado: false
  }),
  methods: {
    registrarProyecto(){
      const proyecto = {
        proyecto: this.proyecto,
        tipo: this.tipo,
        urgente: this.urgente,
        completado: this.completado
      }
      this.proyectos.push(proyecto)
      this.proyecto = ""
      this.tipo= ""
      this.urgente= false
    },
  },
  computed: {
    numeroProyectos(){
      return this.proyectos.length
    },
    porcentaje(){
      let completados = 0
      this.proyectos.map(proyecto =>{
        if(proyecto.completado){
          completados++;
        } 
      })

        return parseInt(completados * 100 / this.numeroProyectos) || 0
      //llamar una propiedad computada en otra
      //this.numeroProyectos // 100% de los proyectos
      
    }
  }
  }
</script>

<style scoped>

  @import url("../assets/formulario.css");

</style>