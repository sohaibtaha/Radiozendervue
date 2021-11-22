<!-- {{infoCaravans[0].name}} -->
<template>

<div>
    <div v-for="(infoCaravans, index) in infoCaravans" :key="infoCaravans.id">
    {{index}}. {{infoCaravans.name}}
    </div>
</div>
</template>

<script>
import axios from 'axios'

  export default {
      mounted () {
    //console.log('testmounted')
    axios
      .get('http://127.0.0.1:8000/api/caravans')
      .then((response) => {
        // console.log('response =', response)
        this.infoCaravans = response.data;
        console.log("this.infoCaravans=",this.infoCaravans)
        })
  },
    data () {
      return {
        infoCaravans: null,


    // data: () => ({
    //   dialog: false,
    //   dialogDelete: false,
    //   headers: [
         
    //       { text: 'name', value: 'name' },
    //       { text: 'platenumber', value: 'platenumber' },
    //       { text: 'capacity', value: 'capacity' },
    //       { text: 'brand', value: 'brand' },
    //       { text: 'chassisnumber', value: 'chassisnumber' },
    //     ],
    //     })
      }
    },
  }
    
</script>