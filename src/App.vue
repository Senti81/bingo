<template>
  <v-app>
    <v-main>
      <Header/>
      <Bingo/>
    </v-main>
  </v-app>
</template>

<script>
import Bingo from './components/Bingo'
import Header from './components/Header'

export default {
  name: 'App',

  components: {
    Bingo,
    Header,
  },

  data: () => ({
    //
  }),
};
</script>
