<template>
    <v-card class="mx-auto">
    <v-card-title class="text-h5 pb-5 grey lighten-2">
        <h1>Login</h1>
    </v-card-title>
    <v-card-text>
        <v-form>
            <v-text-field
                label="Username"
                prepend-icon="mdi-account-circle"
                v-model="inaam"
            />
            <v-text-field
                :type="showPassword ? 'text' : 'password'"
                label="Password"
                v-model="pw"
                prepend-icon="mdi-lock"
                :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off' "
                @click:append="showPassword = !showPassword"
            />
        </v-form>
    </v-card-text>
    <v-divider></v-divider>
    <v-card-actions>
        <!-- <v-btn color="success">Register</v-btn> -->
        <v-btn color="info" @click="handleLogin">Login</v-btn>
        <v-spacer></v-spacer>
        <v-btn color="message" @click="clearLogin">clear</v-btn>
    </v-card-actions>
</v-card>
</template>

<script>
export default {
  name: 'Inlog',

  data () {
    return {
      showPassword: false,
      inaam: '',
      pw: ''
    }
  },
  methods: {
    handleLogin: function () {
      console.log('this.inaam=', this.inaam)
      this.clearLogin()
    },
    clearLogin: function () {
      console.log('wis inputs')
      this.pw = ''
      this.iname = ''
    }
  }
}
</script>
