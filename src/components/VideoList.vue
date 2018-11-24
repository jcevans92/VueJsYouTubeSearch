<template>
    <ul>
        <VideoListItem 
            v-for="video in videos" 
            :video="video"
            :key="video.etag"
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
    } // Properties that will come from parent component, Use object for type checking, Recommended!
};
</script>

<style>

</style>
