<template>
  <v-container fluid>
    <v-row
      v-for="n in 4"
      :key="n"
      no-gutters
    >
      <v-col
        v-for="k in 4"
        :key="k"
        cols="3"
      >
        <v-card
          class="text-center"
          :dark="shuffled[k+(n*4)-5].isActive"     
          outlined
          tile
          elevation="6"
          height="100px"
          width="100px"
          @click="shuffled[k+(n*4)-5].isActive = !shuffled[k+(n*4)-5].isActive"
        >
        <small>
          {{ shuffled[k+(n*4)-5].text }}
        </small>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data:() => ({
    items: [
      { text: 'Witze über Vegetarier 🙈', isActive: false},
      { text: 'Dirk mal wieder zu laut', isActive: false},
      { text: 'Opa geht 🚬', isActive: false},
      { text: 'Oma geht 🚬', isActive: false},
      { text: 'Mimimi...das ist sooo eng hier 😭', isActive: false},
      { text: 'Weibliche Person trinkt nen Kurzen', isActive: false},
      { text: 'Dirk / Opa fängt an zu singen 🎵', isActive: false},
      { text: 'Ein 🍺 kippt um', isActive: false},
      { text: 'Ein 🥩 für Judith übrig lassen', isActive: false},
      { text: 'Puuh...ist das warm hier 🥵', isActive: false},
      { text: 'Männliche Person trinkt nen Kurzen', isActive: false},
      { text: 'Das 🍺 ist zu warm', isActive: false},
      { text: 'Männliche Person muss aufs 🚽', isActive: false},
      { text: 'Oma darf mal wieder nicht ausreden', isActive: false},
      { text: 'Gejammere über Schulbeginn 😟', isActive: false},
      { text: 'Weibliche Person muss aufs 🚽', isActive: false},
      { text: 'Anselm weiß mal wieder alles besser', isActive: false},
      { text: 'Hier nicht rubbeln, sonst kein Gewinn!', isActive: false},
      { text: 'Toll, eure neue Küche 👍', isActive: false},
    ],
    shuffled: [],
  }),
  methods: {
    shuffle(a) {
      var j, x, i;
      for (i = a.length - 1; i > 0; i--) {
        j = Math.floor(Math.random() * (i + 1));
        x = a[i];
        a[i] = a[j];
        a[j] = x;
      }
      return a;
    }
  },
  created() {
    this.shuffled = this.shuffle(this.items)
    // window.addEventListener('beforeunload', function(event) {
    //   event.returnValue = 'Write something'
    // })
  }
}
</script>