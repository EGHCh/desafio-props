<template>
  <div class="d-flex" >
    <p>{{ tarea }}</p>
    <button class="btn btn-primary" @click="eliminarTarea">Eliminar</button>
  </div>
</template>

<script>
export default {
  name: 'TareaComponent',
  data: () => ({
  }),
  emits: ['eliminar:tarea'],
  props: {
    tarea: String
  },
  methods: { 
    eliminarTarea: function (e) {
      this.$emit('eliminar:tarea', e)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
