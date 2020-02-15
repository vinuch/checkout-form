<template>
  <div class="card-bg selected">
    <img :src="imgUrl" alt="">
  </div>
</template>

<script>
export default {
  props: {
    imgUrl: String,
  },
};
</script>

<style scoped>
  .card-bg {
    width: 70%;
    height: 17.5rem;
    border-radius: 20px;
    box-shadow: 1px -1px 11px #b3aeae;
    margin: 0 3rem 3rem;
}


.card-bg img {
  width: 16rem;
  margin: 5% 25%;
}

@media (max-width: 400px) {
  .card-bg {
    width: 70%;
    height: 10rem;
    margin: 0 3rem 3rem;
  }

  .card-bg img{
    width: 9rem;
    margin: 7% 13%;
  }
}
</style>
