<template>
  <div id="maestro">
    <ul v-if = "personas">
      <li v-on:click= "showDetalle" v-for= "persona in personas" v-bind:id = "persona.Id">{{persona.Nombre +" "+persona.Apellidos}}</li>
    </ul>
    <p><input type="button" name="crear" value="Nueva Persona" v-on:click = "showDetalle"/></p>
    <div id="detalle"></div>
  </div>

</template>

<script>
  import $ from 'jquery'
  import Detalle from './Detalle.vue'
  import Vue from 'vue'
  export default {
    name: 'maestro',
    data () {
      return {
        personas: []
      }
    },
    created(){
      $.ajax ({
        type: 'get',
        url:"http://10.60.23.11:59446/api/Persona",
        success: (result)=>{
          this.personas = result;
        }
      })
    },
    methods:{

      showDetalle: function(event){
        let persona = this.personas.filter(persona => persona.id = event.target.id)[0]
        new Vue({
          el: '#detalle',
          data:{
            persona:persona
          },
          render: h => h(Detalle)
        })
      }
    }
  }
</script>
<style>
  li{
    list-style: none;
    border: black 1px solid;
    padding: 10px 20px 10px 20px;
    display: inline;
  }
</style>