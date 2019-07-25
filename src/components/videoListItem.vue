<template>
    <li @click="onVideoSelect">
        <img v-bind:src="thumbnailUrl" />
        {{video.snippet.title}}
    </li>
</template>

<script>
    export default {
        name: 'VideoListItem',
        props: ['video'],
        computed: { //use computed for refactoring data and shortening reference
            thumbnailUrl(){
                return this.video.snippet.thumbnails.default.url; //this.video to reference to prop "video"
            }
        },
        methods: {
            onVideoSelect(){
                this.$emit('videoSelect', this.video)
            }
        }
    }
</script>