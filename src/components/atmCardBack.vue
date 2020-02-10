<template>
  <div>
      <div class="atm">
    <div id="card-number">{{ cardNumber }}</div>
    <!-- <input type="number" placeholder="" id="card-number"> -->
    <div class="row">
      <div>
        <span class="label">name</span>
        <div class="value" >{{ cardName }}</div>
        <!-- <label for="name">name</label><br>
        <input type="text" name="name" id="card-name" placeholder=""> -->
      </div>
      <div>
        <span class="label">expiration date</span>
        <div class="value">{{ expDate }}</div>
        <!-- <label for="expiry-date">expiration date</label><br>
        <input type="date" name="expiry-date" id="card-name"> -->
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  //
};
</script>

<style scoped>

</style>
