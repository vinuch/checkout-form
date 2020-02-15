<template>
  <div>
      <div class="atm">
        <div class="row">
          <div id="black-box"></div>
          <div class="cvv">
            <span class="cvv">CVV</span>
            <div class="cvv-display value" >{{ cvv }}</div>
          </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cvv: {
      type: Number,
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
      /* position: absolute; */
      top: 5rem;
    }
    #black-box {
      height: 4rem;
      width: 70%;
      background-color: black;
      margin-top: .5rem;
    }
    .row {
      display: flex;
      justify-content: space-between;
    }
    input {
      background: #fff;
      border: none;
      width: 100%;
      padding: .5rem;
    }
    .cvv {
      margin-left: 1rem;
    }
    .cvv-display {
      background-color: #fff;
      width: 100px;
      height: 2.5rem;
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

    @media (max-width: 500px) {
      .atm {
        width: 85%;
        margin: 0 -1.5rem;
      }
    }
</style>
