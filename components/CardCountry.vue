<template>
    <div>
        <v-card height="16vh" elevation="10" class="animate-x rounded-xl" width="90%">
            <v-card-text>
            <v-row>
                <div class="card-image-float">
                    <v-img alt="img" width="100%" :src="content.icon"></v-img>
                </div>

                <div class="d-flex mx-auto align-self-center align-content-center align-center">
                    <span class="black--text font-weight-medium text-h4 text-type-bebas">{{content.temp}}°</span>
                    <v-divider
                    class="mx-3"
                    vertical
                    ></v-divider>
                    <label class="black--text" for="">{{content.name}} <br> {{content.subName}}</label>

                </div>
            </v-row>

            <v-row class="d-flex justify-space-between align-center px-2" align="center">
                <p>Humidity {{content.humidity}}%</p>
                <p>{{content.coor}}</p>
                <p>{{content.speed}}km/h</p>

            </v-row>

            </v-card-text>
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