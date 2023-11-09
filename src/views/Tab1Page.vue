<style>
table {
  border-collapse: collapse;
  width: 100%;
}

tr,
th {
  border: 1px solid black;
  padding: 8px;
}

td {
  border: 1px solid black;
  padding: 8px;
}

template {
  border: 1px solid black;
}</style>

<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Cryptocurrency App</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <ion-button id="open-toast" expand="block" @click="fetchCryptos">Get Data</ion-button>
      <ion-list>
      <ion-item>
        <ion-label>
          <table style="border-collapse: collapse; width: 100%;">
            <tr>
              <th>Nama</th>
              <th>Simbol</th>
              <th>Harga (USD)</th>
            </tr>
            <tr v-for="crypto in cryptos" :key="crypto.id">
              <td>{{ crypto.name }}</td>
              <td>{{ crypto.symbol }}</td>
              <td>{{ crypto.price_usd }}</td>
            </tr>
          </table>
        </ion-label>
      </ion-item>
    </ion-list>
      <ion-toast trigger="open-toast" message="Data Cryptocurrency berhasil di tampilkan" :duration="5000"></ion-toast>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonButton, IonHeader, IonContent, IonToolbar, IonTitle, IonToast } from '@ionic/vue';
import { defineComponent } from 'vue';
import Axios from 'axios'; // Tambahkan ini

export default defineComponent({
  components: {
    IonButton,
    IonHeader,
    IonContent,
    IonToolbar,
    IonTitle,
    IonToast,
  },
  data() {
    return {
      cryptos: []
    };
  },
  methods: {
    fetchCryptos() {
      // Mengambil data dari API
      Axios.get('https://api.coinlore.net/api/tickers/')
        .then(response => {
          this.cryptos = response.data.data;
        })
        .catch(error => {
          console.error('Error:', error);
        });
    }
  }
});
</script>
