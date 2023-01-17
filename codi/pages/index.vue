<template>
  <v-container>
    <v-row>
      <v-col>
        <div v-if="respostaTest">
          <h1 style="font-size:10vh"> AQUÍ VA EL MISSATGE</h1>
          <pre>
          {{ respostaTest.data.info }}
        </pre>
        
        </div>
        <v-btn @click="testejarApi()">test</v-btn>
     </v-col>
    </v-row>
  </v-container>
  
</template>

<script>
export default {
  data(){
    return{
      respostaTest:null
    }
  },
  methods:{
    testejarApi(){
      console.log('Provant api...')
      let self = this
      this.$axios.get('https://last-one-smo-4w3qk.ondigitalocean.app/api')
      // Quan acabi
      .then(
        resposta=>{
          console.log("M'he descarregat les dades bé", resposta.data)
          self.respostaTest = resposta
        }
      )
      // Si hi ha errors
      .catch(
        error=>{
          console.log("M'he descarregat les dades malament", error)
        }      
      )
    }
  }
}
</script>
