<template>
  <div id="app">
    <start-screen v-if="page === 1" @switch-screen="switchPage"></start-screen>
    <star-wars v-else-if="page === 2" @switch-screen="switchPage"></star-wars>
    <pou-screen v-else-if="page=== 3" @grow-up="growUp" :astroid="age"></pou-screen>
    <game v-else-if="page===4"></game>
  </div>
</template>
 
<script>
import StartScreen from 'src/components/StartScreen.vue';
import StarWars from 'src/components/StarWars.vue';
import PouScreen from 'src/components/PouScreen.vue';
import Game from 'src/components/Game.vue';

export default {
  name: "app",
  data() {
    return {
      page: 1,
      age: "baby" , 
    }
  },
  components: {
    StartScreen , 
    StarWars,
    PouScreen,
    Game
  },
  methods: {
     switchPage(Page) {
      this.page = Page;
    },
    growUp(currAge) {
      if (currAge === "done") {
        this.switchPage(this.page+1);
      } else {
        this.age = currAge;
      }
    }
  }
}

</script>

<style>
@font-face {
  font-family: "amnon";
  src: url(./assets/fonts/amnon.ttf);
}

@font-face {
  font-family: "kshafim";
  src: url(./assets/fonts/kshafim.ttf);
}


#app {
  direction: rtl;
  width: 100%;
	height: 100%;
  font-family: "kshafim";
  overflow: hidden;
}
</style>