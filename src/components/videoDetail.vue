<template>
    <div v-if="video"> 
        <!-- v-if = if video prop is not null -->
        {{video.snippet.title}}
    </div>
</template>

<script>
    export default {
        name: 'VideoDetail',
        props: ['video']
    }
</script>