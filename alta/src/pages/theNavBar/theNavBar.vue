<template>
  <nav id="the-nav-bar">
    <ul>
      <li v-for="lien in liens">
        <a href="#">{{ lien.title }}</a>
      </li>
    </ul>
  </nav>
</template>
<script setup>
const liens = [
  {
    title: "Placeholder",
    summary: "Placeholder summary",
    route: "",
  },
  {
    title: "Activité professionnelle",
    summary: "Placeholder summary",
    route: "",
  },
  {
    title: "Ma formation",
    summary: "formation summary",
    route: "",
  },
  {
    title: "Mes projets",
    summary: "projets summary",
    route: "",
  },
];
</script>
