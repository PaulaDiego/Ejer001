<template>
<div id="detalle">

<p><label for="nombre">Nombre:</label><input type="text" name="nombre" id="nombre" v-model="person.Nombre"></p>
<p><label for="apellidos">Apellidos:</label><input type="text" name="apellidos" id="nombre" v-bind:value="person.Apellidos"/></p>
<p><label for="edad">Edad:</label><input type="number" name="edad" id="nombre" v-bind:value="person.Edad"/></p>
<p><input type ="button" name="aceptar" value="Aceptar" v-on:click="send"/></p>
</div>
</template>

<script>
import $ from 'jquery'
export default {
	name: 'detalle',
	data(){
		person:this.person
	}
	created(){
		if(this.$parent._data.persona != undefined){
			this.person = this.$parent._data.persona
			console.log(this.$parent)
		}else{
			this.person = {
				Nombre: "",
				Apellidos: "",
				Edad: null,
				Id:null
			}
		}

	},
	methods: {
		send: function(event){
			/*if(this.persona.Id ==null){
				$.ajax ({
					type: 'post',
					url:"http://10.60.23.11:59446/api/Persona",
					data: this.person.serialize(),
					success: (result)=>{
						console.log("ENVIADO")
					}
				})
			}else{
				$.ajax ({
					type: 'put',
					url:"http://10.60.23.11:59446/api/Persona"+this.persona.Id,
					data: this.persona,
					success: (result)=>{
						console.log("ENVIADO")
					}
				})
			}*/
			console.log(person)
		}
	}
}
</script>

<style>
#detalle{
	text-align:center;
}

</style>