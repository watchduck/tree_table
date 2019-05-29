<template>
  <div id="app">

    <p v-if="error" id="error">
      {{error}}
    </p>

    <div v-if="!showResults">
      <intro-text></intro-text>
      <textarea rows="10" v-model="input"></textarea>
      <button @click="post">create table</button>
    </div>
    <results v-else></results>

  </div>
</template>

<script>
  import IntroText from './components/IntroText.vue';
  import Results from './components/Results.vue';

  export default {
    data() { return {
      input: ''
    }},
    computed: {
      showResults() { return this.$store.state.showResults },
      output() { return this.$store.state.output },
      error() { return this.$store.state.error }
    },
    methods: {
      post() {
        this.$store.dispatch('actPost', this.input)
      }
    },
    components: {Results, IntroText}
  }
</script>

<style lang="scss">
  @import "~styles/style.scss";
</style>

