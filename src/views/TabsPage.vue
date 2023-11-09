<style>
ion-tab-bar {
  background-color: rgb(66, 66, 255);
  color: azure;
  font-size: 10px;
  box-shadow: black inset;
}

template {
  border: 1px solid black;
}
</style>
<template>
  <ion-page>
      <ion-tabs>
        <ion-router-outlet></ion-router-outlet>
        <ion-tab-bar slot="bottom">
          <h5>Daftar Cryptocurrency</h5>
        </ion-tab-bar>
      </ion-tabs>
    </ion-page>
</template>

<script setup lang="ts">
import { IonTabBar, IonTabButton, IonTabs, IonLabel, IonIcon, IonPage, IonRouterOutlet } from '@ionic/vue';
import { ellipse, square, triangle } from 'ionicons/icons';
</script>
