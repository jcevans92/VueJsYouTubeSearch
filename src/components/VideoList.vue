<template>
    <ul>
        VideoList
        {{ videos.length }}
    </ul>
</template>
    
<script>
export default {
    name: 'VideoList',
    props: {
        videos: Array
    } // Properties that will come from parent component, Use object for type checking, Recommended!
};
</script>

<style>

</style>
