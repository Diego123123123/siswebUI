<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>NEWSPAPERS</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <!-- <v-btn
              flat
              target="_blank"
      >
        <router-link to="news"><span class="mr-2">CREAR NOTICIA</span></router-link>

      </v-btn> -->
      <router-link to="news"><span class="mr-2">CREAR NOTICIA</span></router-link>
    </v-toolbar>

    <v-content>
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Home from './views/Home'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Home
  },
  data () {
    return {
      //
    }
  }
}
</script>
