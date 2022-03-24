<template>
  <div class="bottom-section">
    <div class="roulette-window">
      <ul>
        <img src="../assets/images/survivor_emblems/EmblemIcon_benevolent_none.webp" class="four-perk" id="roulette-1"/>
        <img src="../assets/images/survivor_emblems/EmblemIcon_evader_none.webp" class="four-perk" id="roulette-2"/>
        <img src="../assets/images/survivor_emblems/EmblemIcon_lightbringer_none.webp" class="four-perk" id="roulette-3"/>
        <img src="../assets/images/survivor_emblems/EmblemIcon_unbroken_none.webp" class="four-perk" id="roulette-4"/>
      </ul>
    </div>
    <div class="button-section">
      <button class="btn-secondary spin-button" v-on:click="SpinButton">Spin</button>
      <div class="drop-down-container" id="drop-container">
        <p class="drop-down-item" v-on:click="PassCategory('.perk-item')">Item</p>      <!-- seems like vue does not like nested "" for the argument -->
        <p class="drop-down-item" v-on:click="PassCategory('.perk-exhaustion')">Exhaustion</p>
        <p class="drop-down-item" v-on:click="PassCategory('.perk-healing')">Healing</p>
        <p class="drop-down-item" v-on:click="PassCategory('.perk-information')">Information</p>
        <p class="drop-down-item" v-on:click="PassCategory('.perk-wiggle')">Wiggle</p>
        <p class="drop-down-item" v-on:click="PassCategory('.perk-looping')">Looping</p>
        <p class="drop-down-item" v-on:click="PassCategory('.perk-support')">Support</p>
        <p class="drop-down-item" v-on:click="PassCategory('.perk-stealth')">Stealth</p>
        <p class="drop-down-item" v-on:click="PassCategory('.perk-secondchance')">Second Chance</p>
        <p class="drop-down-item" v-on:click="PassCategory('.perk-diversion')">Diversion</p>
      </div>
      <button class="btn-secondary reset-button" v-on:click="ResetButton">Reset</button>
    </div>
  </div>
</template>

<style scoped>
  .bottom-section {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
  }
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

  .button-section {
    display: flex;
    justify-content: space-around;
  }

  .drop-down-container {
    max-height: 75px;
    overflow:auto;
  }
  /* lifted from bootstrap */
  .btn-secondary {
    color: #fff;
    background-color: #6c757d;
    border-color: #6c757d;
    max-height: 25px;
  }
  .btn-secondary:hover {
    color: #fff;
    background-color: #5c636a;
    border-color: #565e64;
  }
  .btn-check:focus + .btn-secondary, .btn-secondary:focus {
    color: #fff;
    background-color: #5c636a;
    border-color: #565e64;
    box-shadow: 0 0 0 0.25rem rgba(130, 138, 145, 0.5);
  }
  .btn-check:checked + .btn-secondary, .btn-check:active + .btn-secondary, .btn-secondary:active, .btn-secondary.active, .show > .btn-secondary.dropdown-toggle {
    color: #fff;
    background-color: #565e64;
    border-color: #51585e;
  }
  .btn-check:checked + .btn-secondary:focus, .btn-check:active + .btn-secondary:focus, .btn-secondary:active:focus, .btn-secondary.active:focus, .show > .btn-secondary.dropdown-toggle:focus {
    box-shadow: 0 0 0 0.25rem rgba(130, 138, 145, 0.5);
  }
  .btn-secondary:disabled, .btn-secondary.disabled {
    color: #fff;
    background-color: #6c757d;
    border-color: #6c757d;
  }
</style>

<script>
  //import PerkDropDownWindow from '@/components/PerkDropDownWindow.vue'
  export default {
    data() {
      return {
        counter: 0,
        category: null,
      }
    },

    methods: {
      SpinButton() {
        this.counter += 1;

        if (this.counter == 1) {
          const allPerks = document.querySelectorAll(".perk");
          let randomOnePerk = Math.floor(Math.random() * allPerks.length);
          const perk1 = document.querySelector("#roulette-1");
          perk1.src = allPerks[randomOnePerk].src;
          perk1.title = allPerks[randomOnePerk].title;

          const perkExplanation = document.querySelector(".perk-description");
          perkExplanation.textContent = "Press spin again to receive a random tier 2 perk!";
        }
        
        else if (this.counter == 2) {
          const tierTwoPerks = document.querySelectorAll(".rating-3");
          let randomTwoPerk = Math.floor(Math.random() * tierTwoPerks.length);
          const perk2 = document.querySelector("#roulette-2");
          perk2.src = tierTwoPerks[randomTwoPerk].src;
          perk2.title = tierTwoPerks[randomTwoPerk].title;

          const perkExplanation = document.querySelector(".perk-description");
          perkExplanation.textContent = "Click an option then spin to receive a random perk from that category!";
        }

        // this one is a bit harder: need to create drop down field then filter based on that
        else if (this.counter == 3 && this.category == null) {
          console.log("INVALID");
          this.counter == 2;
          const spinButton = document.querySelector(".spin-button");
          spinButton.disabled = true;

          const perkExplanation = document.querySelector(".perk-description");
          perkExplanation.textContent = "ERROR: You must select a perk category."
        }

        else if (this.counter == 3 && this.category != null) {
          console.log("SELECT");

          const categoryPerk = document.querySelectorAll(this.category);
          console.log(categoryPerk);

          let randomThreePerk = Math.floor(Math.random() * categoryPerk.length);
          const perk3 = document.querySelector("#roulette-3");
          perk3.src = categoryPerk[randomThreePerk].src;
          perk3.title = categoryPerk[randomThreePerk].title;

          const perkExplanation = document.querySelector(".perk-description");
          perkExplanation.textContent = "Free choice! Click any perk to add that to your build."
        
          // emit event to share data to app.vue, which will get passed as a prop back down to perks.vue
          this.$emit('counter', 4);
        }

        // this is the hardest filter: need to pass the counter prop into perks.vue, then each of 
        // those perks can be clicked on. PROPS/COMPONENTS: READ
      },

      ResetButton() {
        this.counter = 0;
        let fourPerks = document.querySelectorAll(".four-perk");
        for (let i = 0; i < 3; i++) {
          fourPerks[i].src = "../assets/images/survivor_emblems/EmblemIcon_benevolent_none.webp";
          fourPerks[i].title = "";
        }

        this.category = null;
      },

      PassCategory(perkCategory) {
        this.category = perkCategory;

        let spinButton = document.querySelector(".spin-button");
        spinButton.disabled = false;

        this.counter = 2;

        const perkExplanation = document.querySelector(".perk-description");
        perkExplanation.textContent = this.category + " selected!";
        
      }
    },
  }
</script>