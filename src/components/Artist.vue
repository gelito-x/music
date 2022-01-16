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
li.artist
	display flex
	margin 10px 0
</style>