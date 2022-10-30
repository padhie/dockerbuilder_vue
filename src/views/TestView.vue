<script lang="ts">
  export default {
    data() {
      return {
        count: 0,
        showCountButton: false,
        buttonColor: 'red'
      }
    },

    methods: {
      increment() {
        this.count++
      },
      toggleCountButton() {
        this.showCountButton = !this.showCountButton;
      },
      toggleButtonColors() {
        this.buttonColor = this.buttonColor === 'red' ? 'green' : 'red';
      }
    },

    // `mounted` is a lifecycle hook which we will explain later
    mounted() {
      this.increment()
    }
  }
</script>

<template>
  <div class="test">
    <h1>This is a test page --asd-</h1>

    <div class="content" :class="[buttonColor]">
      <button @click="toggleCountButton"> toggle count </button> &nbsp;
      <button @click="toggleButtonColors"> toggle color </button>
      <br />
      <button v-if="showCountButton" @click="increment"> {{ count }} </button>
    </div>
  </div>
</template>

<style>
  .content.red button {
    background-color: red;
  }
  .content.green button {
    background-color: green;
  }

  button {
    border: 0;
  }

  @media (min-width: 1024px) {
    .test {
      margin-top: 45%;
      min-height: 50vh;
      /*display: flex;*/
      align-items: center;
    }
  }
</style>
