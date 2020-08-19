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

export default {
  name: 'App',

  components: {
    Bingo,
  },

  data: () => ({
    //
  }),
};
</script>
