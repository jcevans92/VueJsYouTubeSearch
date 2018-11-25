<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"></SearchBar>
        <div class="row">
            <VideoDetail :video="selectedVideo" />
            <!--<VideoList v-bind:videos="videos"></VideoList>--><!-- Bind with v-bind -->
            <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList><!-- Bind with :-->
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY = 'AIzaSyAOw2-eg17-NkFyOiwBKy4QBUx8RVrIfKM';

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList,
        VideoDetail
    },
    data() { // Because component. This needs to be function
        return {
            videos: [],
            selectedVideo: null
        };
    },
    methods: {
        onTermChange(searchTerm) {
            
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params:{
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            }).then(response => {
                this.videos = response.data.items;
            });
        },
        onVideoSelect(video) {
            this.selectedVideo = video;
        }
    }
};
</script>