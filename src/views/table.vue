<template>

  <v-data-table v-if='infoCaravans'
    :headers="headersCaravans"
    :items="infoCaravans"
    :items-per-page="5"
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
        headersCaravans: [
          
          { text: 'Naam', value: 'name' },
          { text: 'id', value: 'id' },
          { text: 'Actions', value: 'actions', sortable: false },
        ],
      }
    },
  methods: { 
    deleteItem (item) {
        this.editedIndex = this.headersCaravans.indexOf(item)
        this.editedItem = Object.assign({}, item)
        this.dialogDelete = true

        axios.delete('http://127.0.0.1:8000/api/caravans/' + item.id, {})
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