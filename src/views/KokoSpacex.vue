<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Spacex Launch Programs</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content>
      <div class="main-container">
        <div class="side-filter">
          Filter
          <ion-card>
            <ion-card-header>
              <ion-card-title>Launch Year</ion-card-title>
            </ion-card-header>
            <ion-card-content>
              Launch Year
            </ion-card-content>
          </ion-card>
          <ion-card>
            <ion-card-header>
              <ion-card-title>Successful Launch</ion-card-title>
            </ion-card-header>

            <ion-card-content>
              Successful Launch
            </ion-card-content>
          </ion-card>
          <ion-card>
            <ion-card-header>
              <ion-card-title>Successful Landing</ion-card-title>
            </ion-card-header>

            <ion-card-content>
              Successful Landing
            </ion-card-content>
          </ion-card>
        </div>
        <div class="main-content">
          <LauncDetails
            v-for="item in spacexLaunches"
            :key="item.flight_number"
            :launch="item"
          />
        </div>
      </div>
    </ion-content>
  </ion-page>
</template>

<script>
import { defineComponent } from "vue";
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonCard,
  IonCardContent,
  IonCardHeader,
  IonCardTitle
} from "@ionic/vue";
import LauncDetails from "../components/LaunchDetail.vue";

export default defineComponent({
  name: "Tab1Page",
  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonCard,
    IonCardContent,
    IonCardHeader,
    IonCardTitle,
    LauncDetails
  },
  data() {
    return {
      spacexLaunches: []
    };
  },
  mounted() {
    fetch("https://api.spacexdata.com/v3/launches")
      .then(response => response.json())
      .then(data => {
        this.spacexLaunches = data;
      });
  }
});
</script>
<style scoped>
.main-container {
  display: grid;
  grid-template-columns: 1fr 2fr;
}
.main-content {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
.launch-data-item {
  display: flex;
  flex-direction: row;
}
</style>
