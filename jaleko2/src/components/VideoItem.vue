<template>
  <div id="item" @click="onVideoSelect">
    <img :src="thumbnailUrl" />
    <div class="descricao">
	{{ video.snippet.title }}
	</div>
  </div>
</template>

<script>
export default {
  name: "VideoItem",
  props: {
    video: Object,
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    },
  },
};
</script>

<style scoped>
#item{
	display: flex;
 	
	align-content : flex-end;
	
	background-color:#6a7bb4;
	margin-bottom: 32px;
	border-radius: 8px;
	padding: 30px;
}
img {
  width: 100px;
  height: 80px;
  margin-right:32px;
}
</style>