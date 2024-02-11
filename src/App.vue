<script setup>
import { onMounted, ref } from 'vue';
import PersonalInfo from './components/PersonalInfo.vue'
import SelectPlan from './components/SelectPlan.vue'
import PickAddons from './components/PickAddons.vue'
import ThankYou from './components/ThankYou.vue'
import FinishingUp from './components/FinishingUp.vue'

const stepState = ref(1)

const numberDiv = document.querySelector('.numberDiv')

const addActive = () => {
  numberDiv.children[stepState.value].classList.add('active')
}

const removeActive = () => {
  numberDiv.children[stepState.value].classList.remove('active')
}

const goBack = () => {
  if (stepState.value > 1) {
    removeActive()
    stepState.value--
    addActive()
  }
}

const nextPage = () => {
  if (stepState.value < 4) {
    removeActive()
    stepState.value++
    addActive()
  }
}

onMounted(() => {
  addActive()
})

</script>

<template>
  <!-- Sidebar start -->
  <div class="sidebar">
    <div class="numberDiv">
      <p class="number">1</p>
      <p class="number">2</p>
      <p class="number">3</p>
      <p class="number">4</p>
    </div>
    <div>
      <div>
        <p>Step 1</p>
        <h3>Your info</h3>
      </div>
      <div>
        <p>Step 2</p>
        <h3>Select plan</h3>
      </div>
      <div>
        <p>Step 3</p>
        <h3>Add-ons</h3>
      </div>
      <div>
        <p>Step 4</p>
        <h3>Summary</h3>
      </div>
    </div>
    <div class="filler-div-50">
      <!-- filler div to set the parent as template-grid-colums: 50% 50% -->
    </div>
  </div>
  <!-- Sidebar end -->

  <div class="stepWrapper">
    <PersonalInfo v-if="stepState == 1" />
    <SelectPlan v-if="stepState == 2" />
    <PickAddons v-if="stepState == 3" />
    <FinishingUp v-if="stepState == 4" />
    <ThankYou v-if="stepState == 5" />
  </div>
  <div class="controls">
    <button @click="goBack">
      Go Back
    </button>
    <button @click="nextPage">Next Step</button>
  </div>
  <div class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. Coded by <a href="#">Your
      Name Here</a>.
  </div>
</template>

<style scoped lang="scss">
* {
  color: hsl(231, 11%, 63%);
}

// sidebar styling
.sidebar {
  .numberDiv {
    .number {
      border-radius: 90px;
      background-color: white;
    }

    .number.active {
      background-color: beige;
    }
  }
}
</style>
