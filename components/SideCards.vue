<template>
    <div>
        <div class="card-side-1">
            <v-img :src="content.icon"></v-img>
            <span class="text-body-1">{{content.type}}</span>
        </div>
        <div class="card-side-2">
            <p class="float-left mt-4">{{content.temp}}</p>
            <small class="font-small">°c</small>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        content:{
            type:Object
        }
    }
}
</script>