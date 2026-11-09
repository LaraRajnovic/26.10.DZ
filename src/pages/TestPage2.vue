
<template>
  <q-page padding>
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
  </q-page>
</template>

<script setup>
import { ref } from 'vue'

const tekst = ref('')

const imena = ref([
  'Lara',
  'David',
  'Luka',
  'Leonardo'
])

function dodajIme() {
  if (tekst.value.trim() !== '') {
    imena.value.push(tekst.value.trim())
    tekst.value = ''
  }
}
</script>
