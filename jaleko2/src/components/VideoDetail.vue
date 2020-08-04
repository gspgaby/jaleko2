<template>
	<div v-if="video" id="card-principal">
		<div id="player">
			<iframe :src="videoUrl" />
		</div>
		<div id="descricao">
			<h4>{{ video.snippet.title }}</h4>
			<p>{{ video.snippet.description }}</p>
		</div>
	</div>
</template>

<script>
export default {
	name: 'videoDetail',
	props: {
		video: Object
	},
	computed: {
		videoUrl() {
			const { videoId } = this.video.id;
			return `https://www.youtube.com/embed/${videoId}`;
		}
	}
}
</script>

<style> 
p, h4 {
	font-size: 16px;
	display: flex;
	justify-content: center;
	
	
}
#player iframe {
	margin-left: 15%;
	margin-top: 6%;
	width: 538px;
	height: 290px;
	
}
#card-principal{
	background-color: #FFFFFF;
	display:block;
	justify-content: center;
	width: 40%;
	height: 600px;
	border-radius:8px;
}
</style>