<template>
    <div class="col-md-8" v-if="video">
        <div class="embed-responsive embed-responsive-16by9">
            <iframe class="embed-responsive-item" :src="videoUrl" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <div class="details">
            <h4>{{ video.snippet.title }}</h4>
            <p>{{ video.snippet.description }}</p>
        </div>
    </div>
</template>

<script>
const YOUTUBE_EMBED_URL = "https://www.youtube.com/embed/";

export default {
    name: 'VideoDetail',
    props: {
        video: Object
    },
    computed: {
        videoUrl() {
            const { videoId } = this.video.id;
            return `https://www.youtube.com/embed/${videoId}`; // Only doing this to show string formatting.
            //return YOUTUBE_EMBED_URL + this.video.id.videoId;
        }
    }
};
</script>

<style scoped>

.details {
    margin-top: 10px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
}

</style>


