<script setup>


</script>

<template>
    <!-- Step 1 start -->
    <div class="step-one-div">
      <h1>Personal info</h1>
      <p class="lightGrey">Please provide your name, email address, and phone number.</p>
      <div class="formPersonalInfo">
        <label>Name</label>
        <input type="text" placeholder="e.g. Stephen King ">
        <label>Email Address</label>
        <input type="text" placeholder="e.g. stephenking@lorem.com">
        <label>Phone Number</label>
        <input type="text" placeholder=" e.g. +1 234 567 890"> Next Step
      </div>
    </div>
    <!-- Step 1 end -->

</template>

<style lang="scss" scoped>
.step-one-div {
  .formPersonalInfo {
    display: flex;
    flex-direction: column; 
  }
}
</style>