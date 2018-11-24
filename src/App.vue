<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <!--<VideoList v-bind:videos="videos"></VideoList>--><!-- Bind with v-bind -->
        <VideoList :videos="videos"></VideoList><!-- Bind with :-->
    </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';

const API_KEY = 'AIzaSyAOw2-eg17-NkFyOiwBKy4QBUx8RVrIfKM';

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList
    },
    data() { // Because component. This needs to be function
        return {
            videos: []
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
        }
    }
};
</script>