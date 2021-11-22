<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

<v-btn to="/" class="mr-2 ml-4 primary">
    <v-icon class="mr-2">mdi-home</v-icon>
    <span class="mr-2">Home</span>
</v-btn>

<v-btn to="/Add" class="mr-2 ml-4 primary">
    <span class="mr-2">Add</span>
</v-btn>

<v-btn to="/about" class="mr-2 ml-4 primary">
    <span class="mr-2">About</span>
</v-btn>

<v-btn to="/table" class="mr-2 ml-4 primary">
    <span class="mr-2">Table</span>
</v-btn>

<v-spacer></v-spacer>

<v-btn to="/login" class="mr-2 ml-4 primary">
    <span class="mr-2">Login</span>
</v-btn>


      <!-- <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn> -->
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  })
}
</script>
