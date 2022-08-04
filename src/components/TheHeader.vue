<template>
  <div class="header">
    <div>
      <h1>Where in the world?</h1>
    </div>
    <div class="theme" @click="toggleTheme">
      <img src="@/assets/moon-icon.svg" alt="" />
      <p>Dark Mode</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "TheHeader",
    mounted() {
    const initUserTheme = this.getTheme() || this.getMediaPreference();
    this.setTheme(initUserTheme);
  },
  data() {
    return {
      userTheme: "light-theme",
    };
  },
  methods: {
    toggleTheme() {
      const activeTheme = localStorage.getItem("user-theme");
      if (activeTheme === "light-theme") {
        this.setTheme("dark-theme");
      } else {
        this.setTheme("light-theme");
      }
    },
    setTheme(theme) {
      localStorage.setItem("user-theme", theme);
      this.userTheme = theme;
      document.documentElement.className = theme;
    },
    getTheme() {
      return localStorage.getItem("user-theme");
    },
    getMediaPreference() {
      const hasDarkPreference = window.matchMedia(
        "(prefers-color-scheme: dark)"
      ).matches;
      if (hasDarkPreference) {
        return "dark-theme";
      } else {
        return "light-theme";
      }
    },
  },
};
</script>

<style scoped>
h1 {
  font-weight: 800;
  font-size: 24px;
  line-height: 33px;
  /* identical to box height */
  color: var(--text-primary-color);
}

.header {
  background: var(--background-color-secondary);
  padding: 20px 60px;
  width: 100%;
  height: 70px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.0562443);
}

.theme {
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 0 8px;
  color: var(--text-primary-color);
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


