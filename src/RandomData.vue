<template>
  <h2>Generate random number</h2>
  <p>[{{ randomNumber }}]</p>
  <button @click="nextRandomNumber">next!</button>

  <h2>Generate random password</h2>
  <p>[{{ randomPassword }}]</p>
  <button @click="nextRandomPassword">next!</button>
</template>

<script>
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup(_, { expose }) {
    const randomPassword = ref("");
    const randomNumber = ref("");

    function generateRandomNumber() {
      return (Math.floor(Math.random() * 999_999_999) + 100_000_000);
    }

    function nextRandomNumber() {
      randomNumber.value = generateRandomNumber();
    }

    function nextRandomPassword() {
      randomPassword.value = generateRandomNumber().toString(36);
    }

    expose({
      nextRandomNumber,
    });

    nextRandomNumber();
    nextRandomPassword();

    return {
      randomNumber,
      nextRandomNumber,
      randomPassword,
      nextRandomPassword,
    }
  },
})
</script>
