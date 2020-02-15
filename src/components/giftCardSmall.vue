<template>
<div class="card-sm">
    <img :src= "imgUrl" alt="dog">
    <span class="bullet"></span>
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
  .card-sm {
    width: 8rem;
    height: 6.5rem;
    border-radius: 20px;
    margin: 0 1rem;
    -box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
    /* box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75); */
    box-shadow: 1px -1px 18px #b3aeae;
    position: relative;
}

.card-sm img {
  width: 5.5rem;
  margin: 10%;
}

.bullet {
  width: 1rem;
  height: 1rem;
  border-radius: 50%;
  position: absolute;
  bottom: -2rem;
  left: 50%;
  border: 1px solid #dadff0;
}

.selected .bullet {
  background-color: #dadef1;
}
  .options {
    display: flex;
  }

  @media (max-width: 400px) {
    .card-sm {
      margin: 0 .3rem;
    }

    .card-sm img {
      width: 4.6rem;
    }
  }
</style>
