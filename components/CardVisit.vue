<template>
    <div class="card-visit white--text animate-z" :style="`background-image: url(${content.image}); height:${content.height};`">
            <v-icon color="white" class="mr-2 mb-10 mt-1 float-left" size="15px">mdi-map-marker</v-icon>
            <span class="font-weight-medium">{{content.title}}</span>
        <p class="font-weight-medium">{{content.subtitle}}</p>
    </div>
</template>

<script>
export default {
    props:{
        content:{
            type:Object
        }
    }
}
</script>