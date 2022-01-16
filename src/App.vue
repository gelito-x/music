<template lang="pug">
  #app
    img(src='https://angel-jadan.github.io/music/dist/logo.png')
      
    h1 Music
    select(v-model="selectCountry") 
      option(v-for="country in countries" 
      v-bind:value="country.value") {{ country.name}} 
    spinner(v-show="loading")
    ul
      artist(v-for="artist in artists" 
      v-bind:artist="artist" 
      v-bind:key="artist.mbid")
</template>

<script>
import Spinner from './components/Spinner.vue'
import Artist from './components/Artist.vue'
import getArtists from './api'

export default {
  name: 'app',
  data () {
    return {
      artists: [],
      countries: [
        { name: 'Ecuador', value:'ecuador'},
        { name: 'Argentina', value:'argentina'},
        { name: 'España', value:'spain'},
        { name: 'Colombia', value:'colombia'}
      ],
      selectCountry: 'ecuador',
      loading: true
    }
  },
  methods:  {
    refreshArtist: function(){
      const self = this
      self.artists = [];
      self.loading = true;
      getArtists(this.selectCountry)
      .then(function (artists) {
        self.loading = false;
        self.artists = artists
      })
    }
  },
  mounted: function () {
    this.refreshArtist();    
  },
  watch: {
    selectCountry: function(){
      this.refreshArtist();    
    }
  },
  components: {
    Artist,
    Spinner
  },
}
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px

h1, h2
  font-weight normal

ul
  display flex
  flex-direction row
  flex-flow row wrap
  justify-content space-around
  justify-items center
a
  color #42b983
</style>
