<template>

<body>

	<div id="app">		
		<SearchBar @searchTermChange="onSearchTermChange"></SearchBar>
		<div id="videos">
			<VideoDetail :video="selectedVideo" />
			<VideoList @videoSelect="onVideoSelect" :videos="videosList"></VideoList>
		</div>	
	</div>
	<Footer/>

</body>
	
</template>

<script>

import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';
import Footer from './components/Footer'
import API_KEY from './config'
                   
export default {
	name: 'App',
	components: {
		SearchBar,
		VideoList,
		VideoDetail, 
		Footer
	},
	data() {
		return {
			videosList: [],
			selectedVideo: null
		};
	},
	methods: {
		onSearchTermChange(newSearch) {
		
			axios.get('https://www.googleapis.com/youtube/v3/search', {
				params: {
					key: API_KEY,
					type: 'video',
					part: 'snippet', 
					q: newSearch 
				}
			}).then(response => {
				this.videosList = response.data.items;
			});
		},
		onVideoSelect(video) {
			this.selectedVideo = video;
		}
	}
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat&display=swap');
body{
	font-family: 'Montserrat', sans-serif;
	background-color: #6a7bb4;
	font-size: 14px;
}
#videos{
	display: flex;
	justify-content: center;
}
</style>

