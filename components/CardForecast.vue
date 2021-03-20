<template>
    <div>
        <v-card class="d-flex my-3 animate-z rounded-xl" elevation="6">
            <div class="card-forecast-img ">
                <v-img alt="img" width="30%" class="float-left" :src="content ? content.icon : ''"></v-img>
                    <p class="font-weight-medium">{{content ? content.day : ''}}</p>
                    <p class="grey--text">{{content ? content.type : ''}}</p>
                
            </div>
            <div class="card-forecast-value">
                <p class="white--text">{{content ? content.tempMax : ''}}° / {{content ? content.tempMin : ''}}°</p>
            </div>
        </v-card>
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