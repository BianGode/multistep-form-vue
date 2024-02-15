<script setup>
import { onMounted, ref } from 'vue';
import PersonalInfo from './components/PersonalInfo.vue'
import SelectPlan from './components/SelectPlan.vue'
import PickAddons from './components/PickAddons.vue'
import ThankYou from './components/ThankYou.vue';
import FinishingUp from './components/FinishingUp.vue';

const stepState = ref(0);
// state for the :
// name, email, phone number
// plan, monthly, yearly
// addons

let numberDiv;

onMounted(() => {
  numberDiv = document.querySelector('.numberDiv');
})

const addActive = () => {
  console.log(numberDiv.children[stepState.value]);
  numberDiv.children[stepState.value].classList.add('active');
}

const removeActive = () => {
  console.log(numberDiv.children[stepState.value]);
  numberDiv.children[stepState.value].classList.remove('active');
}
  
const goBack = () => {
  if (stepState.value > 0) {
    removeActive()
    stepState.value--
    addActive()
  }
}

const nextPage = () => {
  if (stepState.value < 3) {
    removeActive()
    stepState.value = stepState.value + 1
    addActive()
  }
}

</script>

<template>
  <!-- Sidebar start -->
  <div class="sidebar">
    <div class="numberDiv">
      <div class="number active">1</div>
      <div class="number">2</div>
      <div class="number">3</div>
      <div class="number">4</div>
    </div>
    <div class="stepWrapper">
      <div class="step">
        <p>Step 1</p>
        <h3>Your info</h3>
      </div>
      <div class="step">
        <p>Step 2</p>
        <h3>Select plan</h3>
      </div>
      <div class="step">
        <p>Step 3</p>
        <h3>Add-ons</h3>
      </div>
      <div class="step">
        <p>Step 4</p>
        <h3>Summary</h3>
      </div>
    </div>
    <div class="filler-div-50">
      <!-- filler div to set the parent as template-grid-colums: 50% 50% -->
    </div>
  </div>
  <!-- Sidebar end -->
  <div class="contentDiv">
    <PersonalInfo v-if="stepState == 0" />
    <SelectPlan v-if="stepState == 1" />
    <PickAddons v-if="stepState == 2" />
    <FinishingUp v-if="stepState == 3" />
    <ThankYou v-if="stepState == 4" />
  </div>
  <div class="controls">
    <button @click="goBack">
      Go Back
    </button>
    <button class="next" @click="nextPage">Next Step</button>
  </div>

  <div class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. Coded by <a href="#">Your
      Name Here</a>.
  </div>
</template>

<style lang="scss">
// mediaquery to set the background for the desktop version
@media only screen and (min-width: 900px) {
  .sidebar {
    background-image: url('assets/images/bg-sidebar-desktop.svg');
    .stepWrapper {
      .step {
        h3 {
          display: none;
        }
      }
    }
  }
}

// Global styling
* {
  color: hsl(231, 11%, 63%);
}
h1, h2, h3, h4 {
  color: hsl(213, 96%, 18%);
}

// sidebar styling
.sidebar {
  background-image: url('./assets/images/bg-sidebar-mobile.svg');
  height: 8rem;
  display: grid;
  grid-template-rows: 50% 50%;
  .stepWrapper {
    display: none;
  }

  .numberDiv {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 1.5rem;
    padding: 50px;
    // height: fit-content;
    // width: fit-content;
    .number {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 2rem;
      width: 2rem;
      border: 1px solid white;
      border-radius: 90px;
      padding: 10px;
      margin: 0;
      color: White;
      background-color: transparent;
    }

    .number.active {
      background-color: beige;
      color:hsl(213, 96%, 18%);
    }
  }
}
.contentDiv {
 width: 90%;
 margin: 0 auto;
 background-color: white; 
}
.controls {
  .next {
    background-color: hsl(243, 100%, 62%);
  }
}
</style>
