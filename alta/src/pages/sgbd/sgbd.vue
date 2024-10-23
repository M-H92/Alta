<template>
  <nav class="lateral-navbar">
    <hr />
    <template v-for="c in components">
      <button @click="setActive(c.key)">
        {{ c.title }}
      </button>
      <hr />
    </template>
    <button @click="displayAll = !displayAll">Tout</button>
  </nav>
  <!-- <main v-if="!displayAll">
    <component :is="getActiveComponent"></component>
  </main>
  <main v-else>
    <template v-for="c in components">
      <component :is="c.value"></component>
      <hr style="margin: 32px 0px" />
    </template>
  </main> -->
  <main>
    <h1>Hello world</h1>
    <h1>Hello world</h1>
    <sgbd_0 />
    <hr />
    <sgbd_1 />
    <hr />
    <sgbd_2 />
    <hr />
    <sgbd_3 />
    <hr />
    <!-- <sgbd_4 />
    <hr /> -->
    <sgbd_5 />
    <hr />
    <sgbd_x />
    <hr />
  </main>
</template>

<script lang="ts" setup>
import sgbd_0 from "./sgbd_0.vue";
import sgbd_1 from "./sgbd_1.vue";
import sgbd_2 from "./sgbd_2.vue";
import sgbd_3 from "./sgbd_3.vue";
import sgbd_5 from "./sgbd_3.vue";
import sgbd_x from "./sgbd_x.vue";

type comp = typeof sgbd_0;
type kvpComponent = { key: number; value: comp; title: string };
const activeComponent = ref(0);
const getActiveComponent = computed(
  () =>
    components.find((c) => c.key == activeComponent.value)?.value ??
    components[0].value
);
const displayAll = ref(false);
const components = [
  {
    key: 0,
    value: sgbd_0,
    title: "Préambule",
  },
  {
    key: 1,
    value: sgbd_1,
    title: "Première DB",
  },
  {
    key: 2,
    value: sgbd_2,
    title: "Relations",
  },
  {
    key: 3,
    value: sgbd_3,
    title: "Contraintes",
  },
  {
    key: 99,
    value: sgbd_x,
    title: "Index",
  },
] as kvpComponent[];
function setActive(key: number) {
  activeComponent.value = key;
  displayAll.value = false;
}
</script>
<style>
.lateral-navbar {
  position: fixed;
  top: 0;
  left: -180px;
  display: flex;
  flex-direction: column;
  width: 200px;
  height: 100vh;
  align-items: stretch;
  background-color: white;
  transition: 0.5s ease-in-out;
  border-radius: 0 5px 5px 0;
  padding: 25px 0px;
  -webkit-box-shadow: 9px 2px 9px -4px rgba(0, 0, 0, 0.5);
  -moz-box-shadow: 9px 2px 9px -4px rgba(0, 0, 0, 0.5);
  box-shadow: 9px 2px 9px -4px rgba(0, 0, 0, 0.5);
}
.lateral-navbar:hover {
  left: 0px;
  transition: 0.5s ease-in-out;
}
.lateral-navbar > button {
  border: none;
  background-color: unset;
  cursor: pointer;
  font-size: 24px;
  padding-top: 8px;
  padding-bottom: 8px;
}
.lateral-navbar > button:hover {
  background-color: rgba(0, 0, 0, 0.1);
}
main {
  padding-top: 2vh;
}
h1 {
  font-size: 3em;
}
section {
  max-width: 50vw;
  margin-left: auto;
  margin-right: auto;
}
</style>
