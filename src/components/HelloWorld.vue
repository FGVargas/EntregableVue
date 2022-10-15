<template>
  <div class="hello">
    <h1 class=" titulo">{{ msg }}</h1>
  <!--  <h1 v-if="author.name == 'Oscar'">Eso es correcto</h1>
    <h1 v-else>Esta mal el author</h1>
    <span>{{ author.books.length == 3 ? 'Si' : 'No'}}</span>
    <br>
    <br>-->
    <!--<li v-for="(value, key) in listaPeces" :key="key"> {{ value }}</li>-->
    <button class="btn btn-success derecha" @click="obtenerPersonajes()"> Actualizar </button>
    <br><br>
    <div  class="d-inline-flex flex-md-equal col-lg-4 pl-md-3  p-0 my-md-3 " v-for="item in listaPersonajes" :key="item._id" >

      <div class="bg-light  text-center  col-12 circulo"   >
      <div class="my-3 p-3">
        <h2 class="display-5"><strong>{{ item.name }}</strong></h2>
        <b-button :to="'/detalle/' + item._id" class="btn btn-success"> Interactuar </b-button>
      </div>
      <img :src=" item.imageUrl" class="bg-dark shadow-sm mx-auto" style="width: 60%; height: 300px; border-radius: 21px 21px 0 0;">
    </div>
  </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    // eslint-disable-next-line vue/require-prop-type-constructor
    msg:"",
  },
  data(){
    return {
      listaPersonajes: []
    }
  },
  created(){
    this.obtenerPersonajes();
  },
  methods:{
    obtenerPersonajes(){
      let apiURL = 'https://api.disneyapi.dev/characters';
      this.listaPersonajes= [];

      this.$http.get(apiURL).then(response => {
        if(response.status == 200){
        let data = response.data.data;
        data.forEach((element, _id) =>{
          if (_id + 1  <= 20){
            this.listaPersonajes.push(element)
          }
        });
        }
      })
      .catch(e => console.log(e))
      .finally(()=>console.log("Se ejecuto el servicio"))
    }
  },
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.circulo{
  border-radius:15px;
  padding:5px;
}
.titulo{
  font:  60px/1 Brush Script MT;
  color: white;
}
</style>
