<template>
  <main class="my-container">
    <h1>Diákok és Szakkörök</h1>
    <div class="row">
      <div class="col-5">
        <table class="table">
          <!-- Táblázat -->
          <thead>
            <tr>
              <th scope="col">Diákok</th>
              <th scope="col">Osztályok</th>
              <th scope="col">Szakkörök</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="diak in diakok" :key="diak.id">
              <td>{{ diak.nev }}</td>
              <td>{{ diak.osztaly }}</td>
              <td>
                <select class="form-select" v-model="diak.szakkorId">
                  <option v-for="szakkor in szakkorok" :key="szakkor.id" :value="szakkor.id">
                    {{ szakkor.nev }}
                  </option>
                </select>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col-7 px-5">
        <div class="sticky-top">
          <!-- Szakkörök -->
          <h2>Szakkörök</h2>
          <SzakkorCard
          v-for="(szakkor) in szakkorok" :key="szakkor.id"
          :szakkor="szakkor"
          :diakok="diakok"
          />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import SzakkorCard from '@/components/SzakkorCard.vue'

export default {
  components: {
    SzakkorCard
  },
  data() {
    return {
      diakok: [
        { id: 1, nev: "Krisztina", osztaly: "1.A", szakkorId: 4 },
        { id: 2, nev: "Bence", osztaly: "2.B", szakkorId: 4 },
        { id: 3, nev: "Zsófia", osztaly: "3.C", szakkorId: 4 },
        { id: 4, nev: "László", osztaly: "4.A", szakkorId: 4 },
        { id: 5, nev: "Anna", osztaly: "5.B", szakkorId: 4 },
        { id: 6, nev: "Miklós", osztaly: "6.C", szakkorId: 4 },
        { id: 7, nev: "Eszter", osztaly: "7.A", szakkorId: 4 },
        { id: 8, nev: "Gábor", osztaly: "8.B", szakkorId: 4 },
        { id: 9, nev: "Réka", osztaly: "1.C", szakkorId: 4 },
        { id: 10, nev: "Dániel", osztaly: "2.A", szakkorId: 4 },
        { id: 11, nev: "Fanni", osztaly: "3.B", szakkorId: 4 },
        { id: 12, nev: "Sándor", osztaly: "4.C", szakkorId: 4 },
        { id: 13, nev: "Maja", osztaly: "5.A", szakkorId: 4 },
        { id: 14, nev: "Tibor", osztaly: "6.B", szakkorId: 4 },
        { id: 15, nev: "Viktória", osztaly: "7.C", szakkorId: 4 }
      ],
      szakkorok: [
        { id: 1, nev: "Foci" },
        { id: 2, nev: "Kosárlabda" },
        { id: 3, nev: "Ping-pong" },
        { id: 4, nev: "Nem jár szakkörre" },
      ]
    }
  }
}
</script>

<style scoped>
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
  background-image: url('https://your-image-url.com/background.jpg'); /* Itt add meg a háttérkép URL-jét */
  background-size: cover;
  background-position: center;
  color: #ffffff; /* Szöveg színe */
}

.my-container {
  background-color: rgba(0, 0, 0, 0.7); /* Félátlátszó háttér a tartalomhoz */
  border-radius: 15px;
  padding: 20px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
}

.table {
  background-color: rgba(255, 255, 255, 0.1); /* Átlátszó háttér a táblázathoz */
  border-radius: 10px;
}

th, td {
  border-bottom: 1px solid rgba(255, 255, 255, 0.3); /* Vékony, fehér vonal a táblázatban */
}

th {
  background-color: rgba(0, 0, 0, 0.5);
  color: #ffcc00; /* Sárga szín */
}

h1, h2 {
  color: #ffcc00; /* Sárga szín */
}

h1 {
  border: 3px solid #ffcc00; /* Sárga keret */
  padding: 10px;
  text-align: center;
}

h2 {
  border: 4px dotted #ffcc00; /* Sárga pöttyös keret */
  padding: 5px;
  text-align: center;
}

.form-select {
  background-color: rgba(255, 255, 255, 0.2);
  color: brown;
  border: 1px solid #ffcc00; /* Sárga szegély */
}

.form-select option {
  background-color: rgba(0, 0, 0, 0.7);
  color: #ffcc00;
}
</style>