<script lang="ts">
export default {
  layout: "default"
};
</script>
<script setup lang="ts">
import { ref } from "vue";
import { useFetch } from "#app";
const searchText = ref("");

const myData = ref([]) as any;
// data.value = await useAsyncData("mashData", () =>
//   $fetch(`/api/hello?search=${searchText.value}`)
// );
// const { data }: { data: any } = await useFetch(`/api/hello?search=girls`, {});
// myData.value = data.value;
// console.log("got back", data.value);

const count = ref(0);
async function searchForStuff() {
  // test = await data.value.json();
  const data = await fetch(`/api/hello?search=${searchText.value}`);
  const json = await data.json();
  console.log("data.value", json);
  myData.value = json;
}
</script>
<template>
  <div>
    <form class="form" @submit.prevent="searchForStuff">
      <input type="text" v-model="searchText" />
      <!-- {{ count }} -->
      <!-- <button @click="count++">Hello</button> -->
      <button>Search For TV Shows</button>
    </form>
    <div class="stuff">
      <div v-for="show in myData">
        <img :src="show.show?.image?.medium" alt="" />
        <!-- {{ show.show.image?.medium }} -->
      </div>
      <!-- {{ myData.show?.image.medium }} -->
      <!-- <img src="/public/taco.jpg" alt="" srcset="" /> -->
    </div>
  </div>
</template>

<style>
.stuff {
  margin-top: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  /* flex-direction: column; */
  gap: 10px;
}

.form {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 100px;
}
</style>
