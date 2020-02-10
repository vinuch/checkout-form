<template>
  <div class="atm">
    <div>
      <img src="../../assets/images/mastercard.png" width="40rem" alt="mastercard">
    </div>
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
</template>

<script>
export default {
  props: {
    cardNumber: {
      type: String,
      required: true,
    },
    cardName: {
      type: String,
      required: true,
    },
    expDate: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
  .atm {
    background: linear-gradient(#dadef1, #f4f5fa);
    height: 12rem;
    width: 60%;
    border-radius: 20px;
    padding: 3rem;
    margin: 0 auto;
  }
  .row {
    display: flex;
    justify-content: space-between;
  }
  input {
    background: none;
    border: none;
    width: 100%;
  }
  .label {
    color: #73769b;
  }
  #card-number {
    color: #3f4178;
    font-family: 'Prompt', sans-serif;
    font-size: 1.5rem;
    margin: 2rem 0;
  }
  .value {
    color: #3f4178;
    font-weight: bold;
    font-size: 1.3rem;
  }
</style>
