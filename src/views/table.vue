<template>

  <v-data-table v-if='infoZenders'
    :headers="headersZenders"
    :items="infoZenders"
    :items-per-page="10"
    class="elevation-1"
  >
  <template v-slot:[`item.actions`]="{ item }">
      <v-icon
        small
        class="mr-2"
        @click="save(item)"
      >
        mdi-pencil
      </v-icon>
      <v-icon
        small
        @click="deleteItem(item)"
      >
        mdi-delete
      </v-icon>
    </template>
    <template v-slot: no-data>
      <v-btn
        color="primary"
        @click="initialize"
      >
        Reset
      </v-btn>
    </template>
  </v-data-table>
</template>

<script>
import axios from 'axios'

  export default {
      mounted () {
    //console.log('testmounted')
    axios
      .get('http://127.0.0.1:8000/api/zenders')
      .then((response) => {
        // console.log('response =', response)
        this.infoZenders = response.data;
        console.log("this.infoCaravans=",this.infoZenders)
        })
  },
    data () {
      return {
        infoZenders: null,
        headersZenders: [
          
          { text: 'programma', value: 'programma' },
          { text: 'id', value: 'id' },
          { text: 'tijd', value: 'duurInMinuten' },
          { text: 'Actions', value: 'actions', sortable: false },
        ],
      }
    },
  methods: { 
    deleteItem (item) {
        this.editedIndex = this.headersZenders.indexOf(item)
        this.editedItem = Object.assign({}, item)
        this.dialogDelete = true

        axios.delete('http://127.0.0.1:8000/api/zenders/' + item.id, {})
      },
    
    save () {
        if (this.editedIndex > -1) {
          Object.assign(this.desserts[this.editedIndex], this.editedItem)
        } else {
          this.desserts.push(this.editedItem)
        }
        this.close()
      },


    },

    
  }
    
</script>