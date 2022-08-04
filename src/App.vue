<template>
    <TheHeader />
    <router-view />
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
export default {
  components: {
    TheHeader,
    TheHeader,
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@200;300;400;600;700;800&display=swap");

#app {
  font-family: "Nunito Sans", sans-serif;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  background: var(--background-color-primary);
}

.header {
  padding: 20px 60px;
  width: 100%;
  height: 70px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
    rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
}
:root{
  --background-color-primary:hsl(0, 0%, 98%);
  --text-primary-color: hsl(200, 15%, 8%);
  --background-color-secondary: hsl(0, 0%, 100%) ;
  --input-color: hsl(0, 0%, 52%)
}
:root.dark-theme{
  --background-color-primary: hsl(207, 26%, 17%);
  --background-color-secondary: hsl(209, 23%, 22%) ;
  --text-primary-color: hsl(0, 0%, 100%);
}


</style>

