<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Daftar Crypto - Tugas 3 MSIM4401 - Agus Setiawan</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Crypto List - Tugas 3 MSIM4401 - Agus Setiawan</ion-title>
        </ion-toolbar>
      </ion-header>

      <div id="container">
        <!-- Button untuk fetch data -->
        <div class="button-container">
          <ion-button @click="fetchCryptoData">Refresh</ion-button>
        </div>

        <ion-list>
        <ion-item v-for="crypto in cryptoList" :key="crypto.id" lines="full">
          <ion-grid>
            <ion-row>
              <ion-col size="2" class="rank">
                <p>Rank</p>
                <h3><strong>{{ crypto.rank }}</strong></h3>
              </ion-col>
              <ion-col size="4" class="details">
                <p>{{ crypto.name }}</p>
                <h3><strong>{{ crypto.symbol }}</strong></h3>
              </ion-col>
              <ion-col size="4" class="price">
                <p>USD</p>
                <h3><strong>{{ crypto.price_usd }}</strong></h3>
              </ion-col>
            </ion-row>
          </ion-grid>
        </ion-item>
      </ion-list>

        <!-- Ketika belum ada data -->
        <p v-if="cryptoList.length === 0" class="no-data-message">
          Belum ada data. Silahkan klik "Get Data" untuk mendapatkan cryptocurrency list.
        </p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { ref } from 'vue';
import axios from 'axios';


// mendefinisikan type data
interface Crypto {
  id: string;
  symbol: string;
  name: string;
  price_usd: string;
  rank: number; // variable baru
}

// State untuk menyimpan data dari API
const cryptoList = ref<Crypto[]>([]);

// fungsi untuk mengambil data dari API
const fetchCryptoData = async () => {
  cryptoList.value = []; // reset data
  try {
    const response = await axios.get('https://api.coinlore.net/api/tickers/');
    // mapping data dari API ke dalam bentuk yang diinginkan
    cryptoList.value = response.data.data.map((item: any) => ({
      id: item.id,
      symbol: item.symbol,
      name: item.name,
      price_usd: parseFloat(item.price_usd).toFixed(2), // format to 2 decimal places
      rank: item.rank, // mapping rank
    }));
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

export default {
  setup() {
    // Panggil fungsi fetchCryptoData saat komponen di-mount
    fetchCryptoData();

    return {
      cryptoList,
      fetchCryptoData,
    };
  },
};
</script>

<style scoped>
#container {
  text-align: center;
  margin-top: 20px;
  padding: 20px;
}

.button-container {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}
.no-data-message {
  margin-top: 20px;
  color: #666;
  font-size: 16px;
  font-style: italic;
}


</style>
