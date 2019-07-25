<template>
    <ul>
        <VideoListItem 
            v-for="singleVideo in videoList" 
            v-bind:video="singleVideo"
            :key="singleVideo.etag"
            @videoSelect="onVideoSelect"> 
            <!-- //videoselect event is triggered in the child -->
            <!-- //v-bind to pass down prop named video to child. prop video represents each item in videolist array -->
        </VideoListItem>
    </ul>
</template>

<script>
    import VideoListItem from './videoListItem';

    export default {
        name: 'VideoList',
        components: {
            VideoListItem
        },
        // props: ['videoList'] //which props we expect to receive
        props: {
            videoList: Array //we expect to receive the array - validation
        },
        methods: {
            onVideoSelect(video){
                this.$emit('videoSelect', video); //emit event to the parent. pass this event from the child to the parent
            }
        }
    }
</script>


<style scoped>
    /* // scoped means this style affects only this component */
</style>