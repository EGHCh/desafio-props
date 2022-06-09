<template>
	<form @submit.prevent="agregarNuevaTarea" class="d-flex align-items-center">
		<div class="d-flex col-4 align-items-center">
			<label for="exampleInput" class="form-label">Tareas</label>
			<input
				v-model="nuevaTarea"
				type="text"
				class="form-control"
				id="exampleInput"
				aria-describedby="emailHelp"
			/>
		</div>
		<button type="submit" class="btn btn-primary">Submit</button>
	</form>
  <div v-if="tareasNuevas[0]">

    <TareaComponent v-for="(tarea, $index) in tareasNuevas" :key="$index" :tarea="tarea" @eliminar:tarea="eliminarTarea($index)"/>
  </div>
</template>

<script>
import TareaComponent from './components/TareaComponent.vue'

export default {
	name: "App",
	data: () => ({
		nuevaTarea: "",
		tareasNuevas: [],
		tareasCompletadas: [],
	}),
	components: { TareaComponent, },
	methods: {
		agregarNuevaTarea() {
			this.tareasNuevas.unshift(this.nuevaTarea);
			this.nuevaTarea = "";
		},
    eliminarTarea(index) {
      this.tareasNuevas.splice(index, 1)
    },
	},
};
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
