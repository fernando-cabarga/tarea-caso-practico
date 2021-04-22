<template>
 
  <div class="formulario">
    <H1 class="tituloFormulario">{{ titulo }}</H1>
  <div class="preEncabezado">

  </div>     
  <div class="encabezado">
      
          <ul class="fa-ul">
            <li><span class="fa-li"><i class="fab fa-twitch"></i></span><span class="fa-ul-text"><strong>Orden:</strong> {{ orden }} </span></li>
            <li><span class="fa-li"><i class="fas fa-calendar-alt"></i></span><span class="fa-ul-text"><strong>Fecha última revisión:</strong> {{ revision }} </span></li>
            <li><span class="fa-li"><i class="fas fa-building"></i></span><span class="fa-ul-text"><strong>Origen:</strong> {{ origen }}</span></li>
          </ul>
  </div>
  <div class="separador"></div>
  <div>
    <table class="tablaSA"></table> 
  </div>
  <div class="texto"> 
      <p v-html="html"></p>
      
  </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: 'Documento',
  props: {
    msg: String
    
  },
  data() {
      return {
          titulo: 'Adquisición y enagenado de acciones llevadas al resultado del ejercicio',
          orden: 'Contable',
          revision: '9 Junio 2020',
          origen: 'Iberley',
          html: 'Sin asignar',
          info: null,
          API: 'https://externo-smartlex-api-contenidos.iberley.es/',
          id: 'casos/70298/{texto}',
          token: '?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6InRlc3QifQ.eyJ1c2VybmFtZSI6Im1jYXJiYWxsb0BpYmVybGV5LmVzIiwiaWQiOiI3MCIsImV4cCI6MTYyODcxNTYwOSwiaWF0IjoxNjE4OTk5Njg5LCJyb2xlcyI6WyJST0xFX1BSRU1JVU0iXSwibWF0IjoiUEUsQ0ksTUUsQURNLEZJLExBIiwiY29sIjoiQ0MsU1VCLExFLENWIiwiZ2MiOiIyIn0.Uw41LkZlOH4eygonf5mezqFegCL7ZWprWnPRjVI6VAw6b5-nnk1QEHIoMKUbFsW4v05IPLzm1fqDEmEt1mvutYJI_Lw38DMXa1Lx1VWGaci5yLIiW5zv1Fnl4q6X0t4JiMQVHiqoF20x8oCWHrLgUL7qZOesvLKl7c8aJ8-jcBqhk5bEq8SN0bdZfy0mFSHZpOzQrgY4_G7yNX2UuiVLIrWYz6a7dlh8lyUTuqoL2dFEAdQ1FKu60xF5EwEAUJvFE1xXemnlqMrYEQNGgfk2LDFtUF002alDWIy8Wbig2sQGqwThNpubALNhp45wF9UZg-yBP-cZnivGd9VSscZ3ByAXNJK88hiHaAlYDXzs811aeQAESfC2ukScFQVqR8jzaHmLe7vS0iS3ikmo9FTo4RJ6Z61MwFw5QOUw1rChNdRN7U96LVNIkLdq7oGBrC4XSgPJxSOTkaGcUFFtJOVLN15RYmvE7AZrnBS-TxCUKAJON3WrpG_dZKPEZmJeiuQTYmzvP1f259aSthzBrF4hbz5DBUK9bBkKIJYY83Y4Fdw2IDvsqFd1ua4rUDHugj6g2tH8BNv4cCFGvW0Huba426DK-NfIUJ02sKQdy-ARpQ546ASWKahykvSsFlRuy9inYurCYA7CzS0SdzaWDfs_uxsmpih1W02ZfS5bQcuI4T8',
          tablaSA: true


      }
  },
  mounted () {
    axios
      .get(this.API + this.id + this.token)
      .then(response => (this.info = response,
      console.log(this.info),
      this.titulo = this.info.data.titulo,
      this.orden = this.info.data.materia,
      this.origen = this.info.data.emisor,
      this.revision = this.info.data.seo_fecha_creacion,
      this.html = this.info.data.html

      ))
      .catch (error =>{
          console.log(error);
      });
  }
}


</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    #app {
        text-align: left  !important;
    }

    .formulario {
        width: auto;
        height: 100%;
        padding: 2%;
        border-top: 4px solid rgb(209, 208, 208);
        border-left: 8px solid rgb(209, 208, 208);

    }
    .tituloFormulario {
        font-family: 'Majerit',serif;
        line-height: 114.285%;
        font-weight: 700;
        color: #000;
        margin: 0 0 .875rem 0;
        letter-spacing: -1px;
        font-size: 42px;
        text-align: left;
        height: 10%;
    }
    .preEncabezado {
        width: 100%;
        height: auto;
        height: 30px;
        background-color:  rgb(209, 208, 208);
        margin-top: 40px;
        margin-bottom: 15px;
    }
   
    .encabezado {
        width: 450px;
        height: auto;
    }
    .lista {
        text-align: left  !important;
        display:inline-block;
    }
    .lista li {
        font-family: "Roboto",Arial,sans-serif;
        font-size: 15px;
        min-width: 270px;
        line-height: 1.42857;
        color: #555;
        font-weight: 400;
    }
    .fa-ul-text {
        text-align: left;
    }

     .separador {
        width: auto;
        height: 2px;
        margin-top: 50px;
        margin-bottom: 50px;
        background-color:  rgb(209, 208, 208);
     }   

     td {
  border: orange 5px solid;
}   
     
    .tabla2 {
        display: table !important;
        border-collapse: separate !important;
        box-sizing: border-box !important;
        text-indent: initial !important;
        border-spacing: 2px !important;
        border-color: grey !important;
    }
    

</style>
