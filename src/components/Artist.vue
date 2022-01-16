<template lang="pug">
	li.artist
	  h2: a(:href="artist.url" target="_blank" v-html="artist.name") {{ artist.image[2]['#text'] }}
	  img(:src="artist.image[2]['#text']") 
</template>

<script>
	export default {
		name: 'artist',
		props: [ 'artist' ]
	}
</script>

<style lang="stylus" scoped> 
li
	margin 5px


li.artist 
	display flex
	flex-direction column
	align-content center
	align-items center
	justify-content space-around

img
	width 200px
	height: 200px	
</style>