<template>
  <div class="atm">
    <div>
      <img src="../../assets/images/mastercard.png" width="40rem" alt="mastercard">
    </div>
    <div id="card-number">{{ cardNumber }}</div>
    <!-- <input type="number" placeholder="" id="card-number"> -->
    <div class="row">
      <div>
        <!-- <label for="name">name</label><br>
        <input type="text" name="name" id="card-name" placeholder=""> -->
        <span class="label">name</span>
        <div class="value">{{ cardName }}</div>
      </div>
      <div>
        <span class="label">expiration date</span>
        <div class="value">{{ expDate }}</div>

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

  @media (max-width: 400px) {
    .atm {
      width: 85%;
      margin: 0 -1.5rem;
      /* jhkgv */
    }
  }
</style>
