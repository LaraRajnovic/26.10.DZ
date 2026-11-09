
<template>
  <q-page padding>

    <!-- Pozdrav i unos imena -->
    <h4>Pozdrav</h4>

    <q-input
      v-model="tekst"
      label="Unesi ime"
      outlined
      @keyup.enter="dodajIme"
    />

    <q-btn
      label="Dodaj ime"
      color="primary"
      class="q-mt-sm"
      @click="dodajIme"
    />

    <h5>Imena kolega</h5>

    <template v-for="(ime, index) in imena" :key="index">
      <p v-if="ime !== 'Ivan'">
        {{ ime }}
      </p>
    </template>


    <!-- QBadge -->
    <div class="q-pa-md q-gutter-sm">

      <q-btn
        push
        color="white"
        text-color="primary"
        label="Unread Mails"
      >
        <q-badge color="orange" floating>
          {{ readmsg }}
        </q-badge>
      </q-btn>

      <q-btn
        dense
        color="purple"
        round
        icon="email"
        class="q-ml-md"
      >
        <q-badge color="red" floating>
          {{ delmsg }}
        </q-badge>
      </q-btn>

    </div>


    <!-- QCard -->
    <div class="q-pa-md row items-start q-gutter-md">

      <q-card class="my-card bg-secondary text-white">

        <q-card-section>
          <div class="text-h6">Our Changing Planet</div>
          <div class="text-subtitle2">by John Doe</div>
        </q-card-section>

        <q-card-section>
          {{ lorem }}
        </q-card-section>

        <q-separator dark />

        <q-card-actions>
          <q-btn flat @click="openMsg()">Open</q-btn>
          <q-btn flat @click="deleteMsg()">Delete</q-btn>
        </q-card-actions>

      </q-card>

    </div>

  </q-page>
</template>


<script setup>
import { ref } from 'vue'

// Unos imena
const tekst = ref('')

const imena = ref([
  'Lara',
  'David',
  'Luka',
  'Leonardo'
])

// QBadge - broj poruka
const readmsg = ref(22)
const delmsg = ref(4)

// Tekst unutar QCard komponente
const lorem = 'Our planet is a beautiful place that we need to protect.'

// Funkcija za dodavanje imena
function dodajIme() {
  if (tekst.value.trim() !== '') {
    imena.value.push(tekst.value.trim())
    tekst.value = ''
  }
}

// QCard - funkcija Open
function openMsg() {
  if (readmsg.value > 0) {
    readmsg.value -= 1
  }

  console.log('read ' + readmsg.value)
}

// QCard - funkcija Delete
function deleteMsg() {
  if (delmsg.value > 0) {
    delmsg.value -= 1
  }

  console.log('delete ' + delmsg.value)
}
</script>


<style scoped>
.my-card {
  width: 100%;
  max-width: 350px;
}
</style>
