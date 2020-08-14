<template>
  <v-container fluid>
    <v-row
      v-for="(y, iY) in cols"
      :key="iY"
      no-gutters
    >
      <v-col
        v-for="(x, iX) in rows"
        :key="iX"
        cols="3"
      >
        <v-card        
          class="text-center pa-1"
          :dark="shuffled[iX + cols*iY].isActive"     
          outlined
          tile
          elevation="6"
          height="100px"
          width="100px"
          @click="clickOnItem([iX + cols*iY])"
        >
        <h6>
          {{ shuffled[iX + 4*iY].text }}
        </h6>
        </v-card>
      </v-col>
    </v-row>
    <v-btn 
      block
      small
      class="mt-5"
      color="primary"
      @click="reset">
      Neu laden
    </v-btn>
  </v-container>
</template>

<script>
export default {
  data:() => ({
    cols: 4,
    rows: 4,
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
      { text: 'Toll, eure neue Küche 👍', isActive: false},
      { text: 'Matz rülpst', isActive: false},
      { text: 'Opa nimmt die 🦷🦷 raus', isActive: false},
      { text: 'Yolli wiederholt sich', isActive: false},
      { text: 'Petra verbessert Dirk', isActive: false},
      { text: 'Anselm googlet was', isActive: false},
      { text: 'Franzi macht sich vor Lachen inne 👖', isActive: false},
      { text: 'Philipp faselt was von 🚗🚕', isActive: false},
      { text: 'Oma nix Englisch', isActive: false},
      { text: 'Matz verbessert Yolli', isActive: false},
      { text: 'Franzi hat Schluckauf', isActive: false},
      { text: 'Anselm liegt auf dem Boden', isActive: false},
      { text: 'Petra nimmt das Anstandsstück', isActive: false},
    ],
    shuffled: [],
  }),
  computed: {
    randomCards() {
      return this.shuffle(this.items)
    }
  },
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
    },
    clickOnItem(id) {
      this.shuffled[id].isActive = !this.shuffled[id].isActive
      localStorage.setItem('bingoCards', JSON.stringify(this.shuffled))
    },
    reset() {
      localStorage.removeItem('bingoCards')
      this.shuffled = this.shuffle(this.items)
      window.location.reload()
    }
  },
  created() {
    if (localStorage.getItem('bingoCards')) {
      this.shuffled = JSON.parse(localStorage.getItem('bingoCards'))
    } else {
      this.shuffled = this.shuffle(this.items)
    }
  }
}
</script>