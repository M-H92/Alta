<template>
  <div>
    <!-- <the-nav-bar /> -->
    <sgbd />
    <!-- <Deutsch /> -->
  </div>
</template>
<script setup>
// import TheNavBar from "~/src/pages/theNavBar/theNavBar.vue";
import sgbd from "~/src/pages/sgbd/sgbd.vue";
import "~/assets/css/reset.css";
import "~/assets/css/style.css";
// import Deutsch from "./src/pages/deutsch/deutsch.vue";

import { onMounted } from "vue";
// import Papa from "papaparse";
onMounted(async () => {
  let response;
  try {
    const path = "data/deutsch.csv";
    // console.log("-------------");
    // console.log("exists?");
    // const file = new FileSystem();

    // console.log("exists?");
    // // console.log(fs.existsSync(path));
    // console.log("-------------");
    response = await fetch(path);
    const text = await response.text();
    const parsedData = Papa.parse(text, { header: true });
    console.log(parsedData.data);
    // console.log("response.ok");
    // const reader = response.body.getReader();
    // console.log(await reader.read());
    // console.log(await ));
    // ("C:\Repos\Alta\alta\assets\data\deutsch.csv");
  } catch (e) {
    console.error("couldn't read");
    console.error(e);
  }
  //   console.log(response);
  //   console.log(await response);
  //   console.log(response.type);
  //   console.log(await response.arrayBuffer());
  console.warn(await response.text());
});
</script>
