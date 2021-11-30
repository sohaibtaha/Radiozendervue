<template>
    <form @submit.prevent="submit">
        <v-text-field
          v-model="programma"
          label="programma"
          required
        ></v-text-field>

      
        <v-text-field
          v-model="datum"
          label="datum"
          required
        ></v-text-field>
      
        <v-text-field
          v-model="tijd"
          label="tijd"
          required
        ></v-text-field>
    
        <v-text-field
          v-model="duurInMintuen"
          label="duurInMintuen"
          required
        ></v-text-field>
     <v-text-field
          v-model="presentator"
          label="presentator"
          required
        ></v-text-field>
      

      <v-btn
        class="mr-4"
        type="submit"
      >
        submit
      </v-btn>
      <v-btn @click="clear">
        clear
      </v-btn>
    </form>
</template>

<script>
import axios from 'axios'
  // import { required, digits, email, max, regex } from 'vee-validate/dist/rules'
  // import { extend, ValidationObserver, ValidationProvider, setInteractionMode } from 'vee-validate'

  export default {
submit () {
    //console.log('testmounted')
    axios
      .post('http://127.0.0.1:8000/api/zenders')
      .then((response) => {
        // console.log('response =', response)
        this.infoZenders = response.data;
        console.log("this.infoZenders=",this.infoZenders)
        })},

    data: () => ({
      programma: '',
      datum: '',
      tijd: '',
      duurInMintuen: '',
      presentator: ''
    }),

    methods: {
      submit () {
        this.$refs.observer.validate()
      },
      clear () {
        this.programma = ''
        this.datum = ''
        this.tijd = ''
        this.duurInMintuen = '',
        this.presentator = ''
      },
    },
  }
</script>
