<template>
    <ul class="list-group">
        <VideoListItem
            v-for="video in videos" 
            :video="video"
            :key="video.etag"
            @videoSelect="onVideoSelect"
            >

        </VideoListItem>
    </ul>
</template>
    
<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videos: Array
    }, // Properties that will come from parent component, Use object for type checking, Recommended!
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video);
        }
    }
};
</script>

<style>

</style>
