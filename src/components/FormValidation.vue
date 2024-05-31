<script setup>
import SignInComponent from './SignInComponent.vue'
import KeyFeaturesComponent from './KeyFeaturesComponent.vue'
import { onBeforeMount, ref } from 'vue'
let imgPath = ref('')

const randomBGPath = () => {
  let randomNumber = Math.floor(Math.random() * 10)
  console.log(randomNumber)
  if (randomNumber > 5) {
    imgPath.value = '../public/NetflixMovieTileBackground.png'
  } else {
    imgPath.value = '../public/GDWebSignInwithNewuserError.png'
  }
}

onBeforeMount(() => {
  // random images
  randomBGPath()
})
</script>

<template>
  <div
    class="bg-container"
    :style="{
      'background-image': `linear-gradient(90deg, #000 0%, #00000089 10%),url(${imgPath})`
    }"
  >
    <div class="bg-gradient-container"></div>
    <SignInComponent class="sign-in-box" />

    <KeyFeaturesComponent />
  </div>
</template>

<style>
template {
}
.bg-container {
  width: 100%;
  min-height: 100vh;

  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  overflow: hidden;
}
.sign-in-box,
.box {
}
.bg-gradient-container {
  width: 100%;
  min-height: 100vh;
  background-color: transparent;
  position: absolute;
  top: 0;
  right: 0;
  background-image: linear-gradient(270deg, #000 0%, #00000026 10%);
}

/*  ..............................Media Query Here............................ */

@media only screen and (max-width: 600px) {
  .bg-container {
    background-image: none;
    background-color: black;
    padding: 0;
    display: block;
  }
}
</style>
