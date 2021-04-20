<template>
 
  <div class="formulario">
    <H1 class="tituloFormulario">{{ titulo }}</H1>
  <div class="preEncabezado">
      <div class="preEncabezadoLeft"></div>
      <div class="preEncabezadoRight"></div>
  </div>     
  <div class="encabezado">
      
          <ul class="fa-ul">
            <li><span class="fa-li"><i class="fab fa-twitch"></i></span><span class="fa-ul-text"><strong>Orden:</strong> {{ orden }} </span></li>
            <li><span class="fa-li"><i class="fas fa-calendar-alt"></i></span><span class="fa-ul-text"><strong>Fecha última revisión:</strong> {{ revision }} </span></li>
            <li><span class="fa-li"><i class="fas fa-building"></i></span><span class="fa-ul-text"><strong>Origen:</strong> {{ origen }}</span></li>
          </ul>
  </div>
  <div class="separador"></div>
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
          token: '?access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6InRlc3QifQ.eyJ1c2VybmFtZSI6Im1jYXJiYWxsb0BpYmVybGV5LmVzIiwiaWQiOiI3MCIsImV4cCI6MTYxODk4NjI4NywiaWF0IjoxNjE4ODI0Mjg3LCJyb2xlcyI6WyJST0xFX1BSRU1JVU0iXSwibWF0IjoiUEUsQ0ksTUUsQURNLEZJLExBIiwiY29sIjoiQ0MsU1VCLExFLENWIiwiZ2MiOiIyIn0.mZ2TlHcpOTlmcsAnINTGJVTextxnWZm9nDk1bVWLWm5jfH0uHuC-uLMN9ruP9N-W0pg6hBY4CQ8iQZ01OXxragYqH-L0WP3M2f_LbVrcG-Bu0TPckU1Wi-ONw-PCU9XXnZzEt-YLHFTNGekPp60crvF5Jb-e3ramqCsrLV0m8l9VUU9tl-vR450x0YcNrJT44o67pvs0-fYBYlfgPWaVZg-pLhWsGrDKi0AVPgUx2g_2NdzavNEHc6wWhzZ90fN13Y2vH6UeQFx49PH237CfbZuBbGt50FxZjTKYBs4xyvYfuPY1ZbsiSciDCrkWZG-4gLRly9WY0CB2BGtJLwV4-FalxISonr9Y4Q286Bwj5MY3mFE6VYi13HffEnUXe47OcfbHnqGjf5VmMsAHBBM3eG5n7AZVbSKOX2esjTftDOgy4fCoPqdEzgElZtna57e5rNGMx8AKj65qX0inpQ949NbeJJD9k7e4MlHFEB1VyxRUZg1RafbESktYdk8S03GIKPLuch1cBjAlABP_BSryuK7ZfkvRpRyVMrzK4ELJbm6vLAcaLKIOVt8iW3DVSK6zJihuTCP_BmfX2kOXn1fLs94FKdW_d8haCIpP6AmNWNCDikAmJwXdNVhK96_JinBYUulaJj41DOf03trzA-LYAP92H-JDqs3sm94E2NCiDTY&_format=json'

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
    /*.preEncabezadoLeft {
        width: 100%;
        height: 30px;
        background-color:  rgb(209, 208, 208);
        float:right;
        margin:10px;
    }*/
    /*
    .preEncabezadoRight {
        width: 25%;
        height: 26px;
        border-bottom: 4px solid  rgb(209, 208, 208);
        float:right;
    }*/
   
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
    .tabla2 {
        display: table !important;
        border-collapse: separate !important;
        box-sizing: border-box !important;
        text-indent: initial !important;
        border-spacing: 2px !important;
        border-color: grey !important;
    }
    .tabla2 tr:first-child td {
        background-color: #58575c !important;
        color: #fff !important;
        font-weight: bold;
    }


</style>
