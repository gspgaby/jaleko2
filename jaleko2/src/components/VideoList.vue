<template>
	<ul>
		<VideoItem 
			v-for="video in videos"
			:video="video"
			:key="video.etag"
			@videoSelect="onVideoSelect">
		
		</VideoItem>
	</ul>
</template>

<script>
import VideoItem from './VideoItem';
export default {
	name: 'VideoList',
	components: {
		VideoItem
	},
	props: {
		videos: Array
	},
	methods: {
		onVideoSelect(video) {
			this.$emit('videoSelect', video);
		}
	}
};
</script>