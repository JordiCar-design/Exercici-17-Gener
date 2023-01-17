<template>
  <v-container>
    <v-row>
      <v-col>
    <h1 style="font-size:10vh"> AQUÍ VA EL MISSATGE</h1>
    <v-btn @click="testejarApi()">test</v-btn>
     </v-col>
    </v-row>
  </v-container>
  
</template>

<script>
export default {
  methods:{
    testejarApi(){
      console.log('Provant api...')
      
    }
  }
}
</script>
