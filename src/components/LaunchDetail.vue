<template>
  <ion-card>
    <ion-card-header>
      <ion-card-title>{{ launch.mission_name }}</ion-card-title>
    </ion-card-header>
    <ion-card-content>
      <img :src="launch.links.mission_patch" />
      <div class="launch-data">
        <div class="launch-data-item">
          <div>Launch Year:</div>
          <div>{{ launch.launch_year }}</div>
        </div>
        <div class="launch-data-item">
          <div>Successful Launch:</div>
          <div>{{ launch.launch_success }}</div>
        </div>
        <div class="launch-data-item">
          <div>Launch Site:</div>
          <div>{{ launch.launch_site.site_name }}</div>
        </div>
      </div>
    </ion-card-content>
  </ion-card>
</template>
<script>
import {
  IonCard,
  IonCardContent,
  IonCardHeader,
  IonCardTitle
} from "@ionic/vue";

export default {
  components: {
    IonCard,
    IonCardContent,
    IonCardHeader,
    IonCardTitle
  },
  props: {
    launch: {
      type: Object,
      required: true
    }
  }
};
</script>
<style scoped></style>
