<script setup>
import { useRoute, useRouter, RouterView } from "vue-router";
import cars from "../data/cars.json";

const route = useRoute();
const router = useRouter();

const carId = parseInt(route.params.id);
const car = cars.find((c) => c.id === carId);

const showContact = () => {
  if (carId === 4) return;
  return router.push(`/cars/${carId}/contact`);
};
</script>

<template>
  <div v-if="car">
    <h1>Car Vue</h1>
    <p>{{ car.name }}</p>
    <p>{{ car.year }}</p>
    <p>{{ car.price }}</p>
    <button @click="showContact">Click me for contact</button>
    <RouterView />
  </div>
  <div v-else>
    <p>Car not found!</p>
  </div>
</template>