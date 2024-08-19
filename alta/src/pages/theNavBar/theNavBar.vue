<template>
  <nav id="the-nav-bar">
    <ul>
      <li v-for="lien in liens">
        <a href="#">{{ lien.title }}</a>
      </li>
      <li>
        <div class="shadow-wrapper">
          <div class="container">
            <div class="content">
              hello <br />
              world
            </div>
          </div>
        </div>
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
<style scoped>
.shadow-wrapper {
  /* filter: drop-shadow(-1px 6px 3px rgba(98, 52, 235, 0.8)); */
  cursor: pointer;
}
div.container {
  width: fit-content;
  height: 50px;
  background: rgba(98, 235, 235, 0.8);
  padding: 0;
  margin: 0;
}
div.container:after {
  content: "";
  display: block;
  position: relative;
  top: -50px;
  left: 28px;
  width: 10px;
  height: 5px;
  background: rgba(98, 52, 235, 0.8);
  z-index: 10;
}
.shadow-wrapper:hover div.container:after {
  transition: top 0.4s ease-in 0s, width 0.5s ease-in 0s,
    height 0.5s ease-out 0.5s;
  top: -54px;
  width: calc(100% - 28px);
  background: rgba(98, 52, 235, 0.8);
  height: 50px;
}

div.container:before {
  content: "";
  display: block;
  position: relative;
  bottom: -50px;
  right: calc(-100% + 40px);
  width: 10px;
  height: 5px;
  background: rgba(98, 52, 235, 0.8);
  z-index: 10;
}
.shadow-wrapper:hover div.container:before {
  transition: bottom 0.4s ease-in 0s, right 0.5s ease-in 0s,
    width 0.5s ease-in 0s, height 0.5s ease-out 0.5s;
  right: 0px;
  bottom: -54px;
  width: calc(100% - 28px);
  background: rgba(98, 52, 235, 0.8);
  height: 50px;
}
div.content {
  width: 180px;
  height: 46px;
  background: rgb(235, 52, 52);
  margin: 4px;
  z-index: 11;
}
div.container,
div.content {
  position: relative;
  overflow: hidden;
  text-align: center;
  clip-path: polygon(
    0 25px,
    25px 0,
    100% 0,
    100% calc(100% - 25px),
    calc(100% - 25px) 100%,
    0 100%
  );
}

div.container:after {
  clip-path: polygon(
    0 4px,
    4px 0,
    100% 0,
    100% calc(100% - 25px),
    calc(100% - 25px) 100%,
    0 100%
  );
}
div.container:before {
  clip-path: polygon(
    0 25px,
    25px 0,
    100% 0,
    100% 100%,
    calc(100% - 25px) 100%,
    0 100%
  );
}
</style>
