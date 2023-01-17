<template>
  <v-container>
    <v-row>
      <v-col>
        <h1 style="font-size:10vh">{{ultimMissatge}}</h1>
        <h4>{{ultimUsuari}}</h4>
        <v-btn @click="enviarMissatge()">enviar</v-btn>

        <!-- <v-btn @click="descarregarUltimText()">ultim text</v-btn> -->
      </v-col>
    </v-row>
  </v-container>
  </template>
  
  <script>
  export default{
    mounted(){

      setInterval(function() {
        console.log("hola")
      }, 5000);
      this.descarregarUltimText()
    },
    data(){
      return{
        respostaTest:null,
        ultimMissatge:"",
        ultimUsuari:""
      }
    },
    methods:{
      testejarApi(){
        console.log('Provant api..')
        let self = this
        this.$axios.get('https://last-one-smo-4w3qk.ondigitalocean.app/api')
          // Quan acabi
          .then(
            resposta=>{
              console.log("M'he descarregat les dades bé",resposta.data)
              self.respostaTest = resposta
              
            }
          )
          // Si hi ha errors
          .catch(
            error=>{
              console.log("M'he descarregat les dades malament",error)
            }
          )
      },
      descarregarUltimText(){
        let self = this
        this.$axios.get('https://last-one-smo-4w3qk.ondigitalocean.app/api/getText')
        .then(
          r=>{
            console.log("S'ha enviat bé")
            // Recollim
            let missatge = r.data.data.missatge
            let usuari = r.data.data.usuari
            // Assignem al data
            self.ultimMissatge = missatge
            self.ultimUsuari = usuari
          }
          
        )
        .catch(
          e=>{
            console.log('Ultim text error', e)
          }
        )
      },
      enviarMissatge(){
        let self = this

        let dades = {
          missatge:"Hola sóc en Jordi C",
          usuari:"J.C."
        }

        let url = 'https://last-one-smo-4w3qk.ondigitalocean.app/api/setText'

        this.$axios.post(url, dades)
          .then(
            r=>{
              console.log("S'ha enviat bé")
              self.descarregarUltimText()
            }
          )
          .catch(
            e=>{

            }
          )
      }
    }
  }
  </script>
