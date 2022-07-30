<template>
  <div class="header">
    <div><h1>Where in the world?</h1></div>
    <div class="theme" @click="toggle">
      <img src="@/assets/moon-icon.svg" alt="" />
      <p>Dark Mode</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "TheHeader",
};
</script>

<style scoped>
h1 {
  font-weight: 800;
  font-size: 24px;
  line-height: 33px;
  /* identical to box height */
  color: #111517;
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
.theme {
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0 8px;
}

@media only screen and (max-width: 600px) {
  .header {
    padding: 30px 16px;
  }
  h1 {
    font-weight: 800;
    font-size: 14px;
    line-height: 20px;
    color: #111517;
  }

  p {
    font-weight: 600;
    font-size: 12px;
    line-height: 16px;
    color: #111517;
  }
}
</style>


