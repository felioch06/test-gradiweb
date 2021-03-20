<template>
  <div class="d-flex">
    <h4 class="my-auto">+ Top Reviews</h4>
    <v-spacer></v-spacer>
    <div class="text-center">
      <v-avatar size="30px" class="rounded-lg mr-n2 border animate-x-n" color="white">
        <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John" />
      </v-avatar>
      <v-avatar size="30px" class="rounded-lg mr-n2 border animate-x-n" color="white">
        <img src="https://i.pinimg.com/474x/5b/b2/1e/5bb21e15d3b96e8276193262414fef88.jpg" alt="John" />
      </v-avatar>
      <v-avatar size="30px" class="rounded-lg mr-n2 border animate-x-n" color="white">
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTA5fuS6dlQqHI08ARrOzxWNfAKgWb74FSQqQ&usqp=CAU" alt="John" />
      </v-avatar>
      <v-avatar size="30px" class="rounded-lg mr-n2 border animate-x-n border-span" color="#7D67F0">
        <span class="white--text">9+</span>
      </v-avatar>
    </div>
  </div>
</template>

<style lang="scss">
    .border{
        border: 2px solid white;
    }

    .border-span{
        border: 2px solid white !important
    }
</style>