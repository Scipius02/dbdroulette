<template>
  <div class="roulette-window">
    <button v-on:click="SpinButton">Spin</button>
    <ul>
      <img src="../assets/images/survivor_emblems/EmblemIcon_benevolent_none.webp" class="four-perk" id="roulette-1"/>
      <img src="../assets/images/survivor_emblems/EmblemIcon_evader_none.webp" class="four-perk" id="roulette-2"/>
      <img src="../assets/images/survivor_emblems/EmblemIcon_lightbringer_none.webp" class="four-perk" id="roulette-3"/>
      <img src="../assets/images/survivor_emblems/EmblemIcon_unbroken_none.webp" class="four-perk" id="roulette-4"/>
    </ul>
    <button v-on:click="ResetButton">Reset</button>
  </div>
</template>

<style scoped>
  .roulette-window {
    padding: 2em;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    /*align-content: center;*/
  }

  ul {
    display: flex;
  }

  img {
    margin: 1em;
    min-height: 75px;
    min-width: 75px;
    max-height: 125px;
    max-width: 125px;
    background-color:gray;
  }

  button {
    height: 75px;
    width: 75px;
    background-color:antiquewhite;
  }
</style>

<script>
  //import PerkDropDownWindow from '@/components/PerkDropDownWindow.vue'
  export default {
    data() {
      return {
        counter: 0,
      }
    },

    methods: {
      SpinButton() {
        this.counter += 1;

        if (this.counter == 1) {
          const allPerks = document.querySelectorAll(".perk");
          let randomOnePerk = Math.floor(Math.random() * allPerks.length);
          console.log(randomOnePerk);
          const perk1 = document.querySelector("#roulette-1");
          perk1.src = allPerks[randomOnePerk].src;
          perk1.title = allPerks[randomOnePerk].title;
        }
        
        else if (this.counter == 2) {
          const tierTwoPerks = document.querySelectorAll(".rating-3");
          let randomTwoPerk = Math.floor(Math.random() * tierTwoPerks.length);
          const perk2 = document.querySelector("#roulette-2");
          perk2.src = tierTwoPerks[randomTwoPerk].src;
          perk2.title = tierTwoPerks[randomTwoPerk].title;
        }

        // this one is a bit harder: need to create drop down field then filter based on that
        else if (this.counter == 3) {
          const perkDescriptionWindow = document.querySelector(".perk-description-window");
          perkDescriptionWindow.display = "block";
          const perkDropDownItems = document.querySelectorAll(".drop-down-item");
          perkDropDownItems.display = "block";
          console.log("SELECT");
        }

        // this is the hardest filter: need to pass the counter prop into perks.vue, then each of 
        // those perks can be clicked on then that passes back to here. PROPS/COMPONENTS: READ
      },

      ResetButton() {
        this.counter = 0;
        const fourPerks = document.querySelectorAll(".four-perk");
        //fourPerks[0].src = "../assets/images/survivor_emblems/EmblemIcon_benevolent_none.webp";
      }
    },
  }
</script>