<template>
    <div>
        <h1 class="titulo">{{fijo}}</h1>
      <b-button to="/" class="btn  regresar"> Regresar </b-button>
      <label class="text-white d-inline-flex">Cambiar Nombre:<input v-model="personaje.name" placeholder="Nuevo Nombre" class="col-lg-7 form-control"></label>
      <div  class="flex-md-equal col-lg-4 pl-md-3  p-0 my-md-3 m-auto" >
        <br>
        <div class="bg-light  text-center  col-12 "   >
          <div class="my-3 p-3">
            <h2 class="display-5"><strong>{{ personaje.name }}</strong></h2>
          </div>
          <img :src=" personaje.imageUrl" class="bg-dark shadow-sm mx-auto" style=" border-radius: 21px 21px 0 0;">
        </div>
      </div>
      <br>
    </div>
</template>

<script>
export default {
    name: 'detalle-info',
    props: {
        id: Number
    },
  data(){
      return{
        idObjeto: Number,
        personaje: [],
        fijo: String
      }
  },
  created() {
      this.idObjeto = this.$route.params.id;
      this.obtenerPersonajes();
  },
  methods:{
    obtenerPersonajes(){
      let apiURL = 'https://api.disneyapi.dev/characters';
      this.listaPersonajes= [];

      this.$http.get(apiURL+'/'+this.idObjeto).then(response => {
        if(response.status == 200){
          this.personaje = response.data;
          this.fijo=response.data.name;
        }
      })
          .catch(e => console.log(e))
          .finally(()=>console.log("Se ejecuto el servicio"))
    }
  }

}
</script>
<style>

.titulo{
  font:  60px/1  Monaco;
  color: white;
}
.regresar{
  margin-right:75%;
  color: white;
  margin-bottom: 15px;
  background: #2c3e50;
}
</style>