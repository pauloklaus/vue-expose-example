<template>
  <h1>Vue Expose Example</h1>
  <p><button @click="pleaseNextNumber">next number</button></p>

  <p>
    <button @click="pleaseNextPassword">next password</button>
    when you click this button nothing happens, and in browser console/debug you will see an error message.
  </p>

  <hr />
  <random-data ref="randomData" />
</template>

<script>
import { defineComponent, ref } from "vue";
import RandomData from "./RandomData.vue";

export default defineComponent({
  components: { RandomData },
  setup() {
    const randomData = ref();

    function pleaseNextNumber() {
      randomData.value.nextRandomNumber();
    }

    function pleaseNextPassword() {
      randomData.value.nextRandomPassword();
    }

    return {
      randomData,
      pleaseNextNumber,
      pleaseNextPassword,
    }
  },
})
</script>
