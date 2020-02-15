<template>
  <div id="app">
    <section class="container">
      <div class="gift">
        <giftsHeader/>
        <giftCardBig
         :imgUrl="bigCardImg"/>
        <div class="options">
          <giftCardSmall
          v-for="gift in gifts"
          :imgUrl="gift.imgUrl"
          :key="gift.id"
          :isActive="gift.isActive"
          v-on:click.native="changeImg(gift.imgUrl); select(gift.id);"
          :class="{selected: gift.isActive}"
          />
        </div>
      </div>
<!--     :class="{selected: isActive}" -->
      <div class="form">
        <div class="flipper">
            <transition name="front">
            <atmCard v-if="!showCard"
              :cardNumber="cardInfo.cardNumber"
              :cardName="cardInfo.cardHolderName"
              :expDate="cardInfo.expDate"/>
          </transition>

          <transition name="back">
            <atmCardBack v-if="showCard"
              :cvv="cardInfo.cvv"/>
          </transition>
        </div>

        <form action="">
          <div>
            <label  for="card-number">cardholder number</label><br>
            <input v-model="cardInfo.cardNumber" type="number" name="card-number" id="card-number" >
          </div>
          <div>
            <label for="card-name">card name</label><br>
            <input v-model="cardInfo.cardHolderName" type="text" name="card-name" id="card-name">
          </div>
          <div class="row">
            <div>
              <label for="expiry-date">exp date</label><br>
              <input  v-model="cardInfo.expDate"
              type="text" name="expiry-date" id="exp-date">
            </div>
            <div>
              <label for="cvv">cvv</label><br>
              <input @focus="showCard = true"
                @blur="showCard = false" type="number" name="cvv" id="cvv"
                v-model="cardInfo.cvv">
            </div>
            <button id="next-btn">Next</button>
          </div>
        </form>
      </div>
    </section>
  </div>
</template>

<script>

import giftCardBig from '@/components/giftCardBig.vue';
import giftsHeader from '@/components/giftsHeader.vue';
import giftCardSmall from '@/components/giftCardSmall.vue';
import atmCard from '@/components/atmCard.vue';
import atmCardBack from '@/components/atmCardBack.vue';
import dog1 from '../assets/images/pug-dog1.jpg';
import dog2 from '../assets/images/pug-dog2.jpg';
import dog3 from '../assets/images/pug-dog3.jpg';

export default {
  name: 'app',
  data() {
    return {
      gifts: [
        {
          id: 1,
          info: '',
          imgUrl: dog1,
          isActive: true,
        },
        {
          id: 2,
          info: '',
          imgUrl: dog2,
          isActive: false,
        },
        {
          id: 3,
          info: '',
          imgUrl: dog3,
          isActive: false,
        },
      ],
      cardInfo: {
        cardHolderName: 'Daniel Osas',
        cardNumber: '5540 #### #### ####',
        expDate: '01/2020',
        cvv: '',
      },
      bigCardImg: dog1,
      showCard: false,
    };
  },
  components: {
    giftCardBig,
    giftCardSmall,
    giftsHeader,
    atmCard,
    atmCardBack,
  },

  methods: {
    select(id) {
      // eslint-disable-next-line no-alert
      this.gifts.forEach((el) => {
        const elem = el;
        if (el.id !== id) {
          elem.isActive = false;
        } else {
          elem.isActive = true;
          // this.$emit('change-img', elem.imgUrl);
        }
      });
    },
    changeImg(url) {
      this.bigCardImg = url;
    },
    showBack() {
      this.showCard = true;
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  overflow-x: hidden;
}
  #app {
    background-color: #dadef1;
    /* height: 90vh; */
    padding: 4rem 0;
    margin: 0;
  }
  .container {
    display: flex;
    /* height: 80vh; */
    justify-content: center;
    padding-bottom: 2rem;
  }
  .gift {
    flex-basis: 40%;
    background-color: #fff;
    padding: 2rem;
    border-radius: 20px;
    margin-right: -2rem;
  }
  .form {
    flex-basis: 45%;
    background-color: #99a8cf;
    margin: -1.5rem 0;
    border-radius: 20px 20px 20px 0;
    padding: 2rem;
    position: relative;
  }
  .form::before {
    content: " ";
    border-bottom: 84.7vh solid #99a8cf;
    border-left: 116px solid transparent;
    border-right: 0px solid transparent;
    height: 0;
    width: 0;
    position: absolute;
    left: -115px;
    top: 8px;
    border-top-right-radius: 0px;
    display: block;
  }
  .options {
    display: flex;
  }

  .selected .bullet {
  background-color: #dadef1;
}

  form {
    margin-top: 4rem;
    position: relative;
  }

  form input {
    width: 100%;
    background: none;
    border: none;
    border-bottom: 1px solid #fff;
    padding: .2rem 0;
    color: #fff;
    font-family:  'Prompt', sans-serif;
    font-size: 1.2rem;
    margin-bottom: 1.5rem;
  }
  form label {
    color: #c9d1ea;
  }
  .row {
    display: flex;
  }
  .row > div input{
    width: 50%;
  }
  #next-btn {
    width: 10rem;
    height: 3rem;
    margin-top: 1rem;
    background-color: #dadef1;
    color: #99a8cf;
    font-size: 1.3rem;
    text-transform: uppercase;
    font-weight: bold;
  }

  .flipper {
    height: 18rem;
    position: relative;
  }
  .front-leave-active {
    animation: rotate 0.6s ease;
  }

  .front-enter-to {
    display: none;
    animation: rotate-reverse 0.6s ease;
    animation-delay: 0.2s;
  }

  .back-enter-active {
    animation: rotate-reverse 0.6s ease;
    animation-delay: 0.6s;
    visibility: hidden;
  }
  .back-leave-active {
    animation: rotate 0.6s ease ;
  }


  @keyframes rotate {
    0% {
      transform: rotateY(0deg)
    }
    100% {
      transform: rotateY(-90deg);
      visibility: visible;
    }
  }

  @keyframes rotate-reverse {
        0% {
      transform: rotateY(-90deg)
    }
    100% {
      transform: rotateY(0deg);
      visibility: visible;
    }
  }

  @media (max-width: 500px){
    .container {
      display: flex;
      justify-content: center;
      flex-direction: column;
    }

    .gift {
    background-color: #fff;
    padding: 3rem 2rem;
    border-radius: 20px;
    /* margin-right: -2rem; */
    width: 75%;
    margin: 0 1rem 1rem;
    }

    .form {
      border-radius: 20px 20px 20px 20px;
    }
  }

</style>
