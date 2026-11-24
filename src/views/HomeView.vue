<script setup>
import { ref, computed } from 'vue'
import road from '@/assets/road.jpg'

const parkeringspladser = ref([
  { id: 1, name: 'a', capacity: 40, availableSpaces: 30 },
  { id: 2, name: 'b', capacity: 25, availableSpaces: 25 },
  {
    id: 3,
    name: 'c',
    capacity: 20,
    availableSpaces: 18,
  },
])

const recommendedParking = computed(() => {
  let best = null
  for (const p of parkeringspladser.value) {
    if (!best || p.availableSpaces / p.capacity > best.availableSpaces / best.capacity) {
      best = p
    }
  }
  return best
})
</script>

<template>
  <main>
    <div id="hero-container">
      <div id="hc-c-left">
        <h2>P-plads overview</h2>
        <div id="overview-scetch">
          <div class="spot">Spot B</div>
          <div class="spot">Spot A</div>
          <div class="spot road">Vej</div>
          <div class="spot">Spot C</div>
          <div class="spot">Zealand</div>
          <div class="spot road">Vej</div>
          <div class="spot">Zealand Zoo</div>
          <div class="spot">Spot D</div>
          <div class="spot road">Vej</div>
        </div>
      </div>
      <div id="hc-c-right">
        <div id="anbefalet-container">
          <h2>Anbefalet parkeringsplads</h2>
          <p id="anbefalet-p">{{ recommendedParking?.name.toUpperCase() }}</p>
        </div>
        <div id="table-container">
          <h2>Table overview</h2>
          <table>
            <thead>
              <tr>
                <th>Parkerings plads</th>
                <th>Procent available</th>
                <th>Ledige pladser</th>
                <th>Komplet antal pladser</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="p in parkeringspladser">
                <td>{{ p.name }}</td>
                <td>{{ (p.availableSpaces / p.capacity) * 100 }}%</td>
                <td>{{ p.availableSpaces }}</td>
                <td>{{ p.capacity }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
#hero-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  min-height: 90dvh;
  width: 100%;
}

#hc-c-left {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  min-height: 90dvh;
  padding: 10dvh 5dvw;
  gap: 1rem;
}

#overview-scetch {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  width: 100%;
  height: 100%;
  gap: 1rem;
}

.spot {
  height: 100%;
  width: 100%;
  content: '';
  color: black;
  display: flex;
  justify-content: center;
  align-items: center;
}

#hc-c-right {
  display: flex;
  flex-direction: column;
  width: 100%;
  min-height: 90dvh;
  padding-top: 10%;
  border-left: 1px solid black;
  align-items: center;
  justify-content: start;
}

#anbefalet-container {
  display: flex;
  flex-direction: column;
  height: 50%;
  width: 100%;
  place-items: center;
}

#anbefalet-p {
  font-size: 3rem;
}

#table-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  width: 100%;
}

table {
  place-self: center;
  width: 80%;
}

thead > tr {
  gap: 1rem;
}

tr {
  height: auto;
  padding: 2rem 0;
  text-align: center;
}
</style>
