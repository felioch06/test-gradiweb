<template>
  <div>
    <v-card class="pad-10 rounded-xl">
      <v-card-text>
        <v-row>
          <v-col cols="12" md="12">
            <Banner></Banner>
            <SideCards :content="tempBogota"></SideCards>
          </v-col>
        </v-row>
        <v-row>
          <v-col
            cols="12"
            sm="12"
            md="3"
            class="order-sm-3 order-md-1 order-xs-4 order-3"
          >
            <h2 class="text-type black--text font-weight-regular mb-10">
              <b>3 Days</b> Forecast
            </h2>
            <CardForecast :content="tempForecast[0]"></CardForecast>
            <CardForecast :content="tempForecast[1]"></CardForecast>
            <CardForecast :content="tempForecast[2]"></CardForecast>
          </v-col>
          <v-col
            cols="12"
            sm="12"
            md="3"
            class="order-sm-2 order-md-2 order-xs-3 order-2"
          >
            <h2 class="text-type black--text font-weight-regular mb-10">
              <b>Place to</b> Visit
            </h2>
            <CardVisit :content="card1"></CardVisit>
          </v-col>
          <v-col
            cols="12"
            sm="12"
            md="3"
            class="order-sm-1 order-md-3 order-xs-2 order-1"
          >
            <TopReviews class="mb-8"></TopReviews>
            <CardVisit :content="card2" class="mb-6"></CardVisit>
            <CardVisit :content="card3"></CardVisit>
          </v-col>
          <v-col
            cols="12"
            sm="12"
            md="3"
            class="order-sm-0 order-md-4 order-xs-1 order-0"
          >
            <CardCountry
            :content="tempParis"
              class="mb-6 d-flex justify-center card-country"
            ></CardCountry>
            <CardCountry :content="tempFrancia" class="mb-6 d-flex justify-center"></CardCountry>
            <CardAdd class="d-flex justify-center"></CardAdd>
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
import moment from "moment";

import Banner from "~/components/Banner.vue";
import CardForecast from "~/components/CardForecast.vue";
import CardVisit from "~/components/CardVisit.vue";
import SideCards from "~/components/SideCards.vue";
import TopReviews from "~/components/TopReviews.vue";
import CardAdd from "~/components/CardAdd.vue";
import CardCountry from "~/components/CardCountry.vue";

export default {
  components: {
    Banner,
    CardForecast,
    CardVisit,
    SideCards,
    TopReviews,
    CardCountry,
    CardAdd,
  },
  data() {
    return {
      tempBogota: {
        temp: 0,
        type: "",
        icon: "",
      },
      tempParis: {
        temp: 0,
        name: "",
        subName: "",
        coor: "",
        icon: "",
        humidity: "",
        speed: ""
      },
      tempFrancia: {
        temp: 0,
        name: "",
        subName: "",
        coor: "",
        icon: "",
        humidity: "",
        speed: ""
      },
      tempForecast: [],

      card1: {
        height: "37vh",
        image:
          "https://www.denvergov.org/content/dam/denvergov/Portals/728/images/StateOfTheCity/PhotosSOTS_BTN.jpg",
        title: "Arab Street",
        subtitle: "Singapore",
        button: false,
      },
      card2: {
        height: "12vh",
        image:
          "https://i.pinimg.com/originals/76/f2/3e/76f23ef08dc1ebabf4589ca0daa1fc14.jpg",
        title: "Art Science",
        subtitle: "Museum",
        button: false,
      },
      card3: {
        height: "21vh",
        image:
          "https://i.pinimg.com/564x/17/28/56/172856bbf31943621eb9afbfbf4c3dc6.jpg",
        title: "Fountain",
        subtitle: "of Wayne",
        button: true,
      },
    };
  },
  mounted() {
    this.getBogota();
    this.getParis();
    this.getFrancia();
    this.getForecast();
  },
  methods: {
    getBogota() {
      this.$http
        .get(
          "http://api.openweathermap.org/data/2.5/weather?q=bogota&units=metric&appid=7787feb596233a8ff23c63eaddb27d9c"
        )
        .then((res) => {
          this.tempBogota.temp = res.body.main.temp;
          this.tempBogota.type = res.body.weather[0].main;
          this.tempBogota.icon = `http://openweathermap.org/img/w/${res.body.weather[0].icon}.png`;
        });
    },
    getParis() {
      this.$http
        .get(
          "http://api.openweathermap.org/data/2.5/weather?q=paris&units=metric&appid=7787feb596233a8ff23c63eaddb27d9c"
        )
        .then((res) => {
          console.log(res);

          this.tempParis = {
              temp: parseInt(res.body.main.temp),
              name: "Paris",
              subName: "Francia",
              humidity: parseInt(res.body.main.humidity),
              coor: "West",
              icon: `http://openweathermap.org/img/w/${res.body.weather[0].icon}.png`,
              speed: res.body.wind.speed
          }
         console.log(this.tempParis);
        });
    },
    getFrancia() {
      this.$http
        .get(
          "http://api.openweathermap.org/data/2.5/weather?q=francia&units=metric&appid=7787feb596233a8ff23c63eaddb27d9c"
        )
        .then((res) => {
          console.log(res);

          this.tempFrancia = {
              temp: parseInt(res.body.main.temp),
              humidity: parseInt(res.body.main.humidity),
              name: "Lyon",
              subName: "Francia",
              coor: "North",
              icon: `http://openweathermap.org/img/w/${res.body.weather[0].icon}.png`,
              speed: res.body.wind.speed
          }
         console.log(this.tempFrancia);
        });
    },

    getForecast() {
      this.$http
        .get(
          "http://api.openweathermap.org/data/2.5/forecast?q=bogota&units=metric&appid=7787feb596233a8ff23c63eaddb27d9c"
        )
        .then((res) => {
          // console.log(res);

            let p = 1
          for (let i = 1; i <= 3; i++) {
            const item = res.body.list[p];
            this.tempForecast.push({
              tempMax: parseInt(item.main.temp_max),
              tempMin: parseInt(item.main.temp_min),
              type: item.weather[0].main,
              day: moment(item.dt_txt).format('dddd'),
              icon: `http://openweathermap.org/img/w/${item.weather[0].icon}.png`,
            });
            p += 9
            console.log(this.tempForecast);
          }
          res.body.list;
          console.log(moment().format("dddd"));
        });
    },
  },
};
</script>
