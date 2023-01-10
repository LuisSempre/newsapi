<template>
  <div class="container" id="app">
    <SourceSelection v-on:sourceChanged="sourceChanged"></SourceSelection>
    <NewsList v-bind:source="source"></NewsList>
  </div>
</template>

<script>
import SourceSelection from './components/SourceSelection'
import NewsList from './components/NewsList'

export default {
  name: 'app',
  components: {
    SourceSelection,
    NewsList
  },
  data () {
    return {
      source: ""
    }
  },
  methods: {
    sourceChanged: function(source){
      this.source = source;
    }
  }
}
</script>

<style>
#app {
  padding-top: 20px;
}
</style>
