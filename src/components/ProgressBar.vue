<template>
    <h3 class="text-center">Progreso: {{ porcentaje }}%</h3>
    <div class="progress mb-3">
        <div class="progress-bar progress-bar-striped progress-bar-animated bg-success"
        role="progressbar"
        :aria-valuenow="porcentaje"
        aria-valuemin="0"
        aria-valuemax="100"
        :style="`width: ${porcentaje}%`"></div>
        <!-- el style es lo que modifica el relleno de la barra -->
    </div>
</template>

<script>
export default {
    props:{
        porcentaje: Number
    }
}
</script>

<style>

</style>