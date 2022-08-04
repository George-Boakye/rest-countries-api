<template>
  <div class="main">
    <div class="back" @click="this.$router.go(-1)">
      <figure class="back-arrow">
        <img src="@/assets/back-arrow.svg" alt="" />
      </figure>
      <h4>Back</h4>
    </div>
    <div class="container">
      <figure>
        <img :src="singleCountry.flags?.png" alt="" />
      </figure>
      <div class="info">
        <h1>{{ singleCountry.name?.common }}</h1>
        <div>
          <div class="upperInfo">
            <div class="left">
              <p>
                Native name: {{ singleCountry.name?.nativeName?.kal?.official }}
              </p>
              <p>Population:{{ singleCountry.population }}</p>
              <p>Region:{{ singleCountry.region }}</p>
              <p>Sub Region:{{ singleCountry.subregion }}</p>
              <p>
                Capital(s):<span
                  v-for="capital in singleCountry.capital"
                  :key="capital"
                >
                  {{ capital }},</span
                >
              </p>
            </div>
            <div class="right">
              <!-- <p>Top Level Domain:{{singleCountry}}</p> -->
              <p>
                Currencies:<span
                  v-for="currency in singleCountry.currencies"
                  :key="currency"
                  >{{ currency.name }},</span
                >
              </p>
              <p>
                Languages:
                <span
                  v-for="language in singleCountry.languages"
                  :key="language"
                  >{{ language }},</span
                >
              </p>
            </div>
          </div>
        </div>
        <div class="lowerInfo">
          <p>
            Border Countries:
            <span v-for="border in singleCountry.borders" :key="border">
              {{ border }}{{ "," + "  " }}</span
            >
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
export default {
  name: "singleView",
  data: () => ({
    // country: "",
  }),
  created() {
    const countryName = this.$route.params.name;
    this.getSingleCountry(countryName);
  },
  computed: {
    ...mapGetters({
      singleCountry: "getSingleCountry",
    }),
  },
  methods: {
    ...mapActions({
      getSingleCountry: "getSingleCountry",
    }),
  },
};
</script>

<style scoped>
.main {
  padding: 40px 60px;
  background: var(--background-color-primary);
  color: var(--text-primary-color);
}
.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  /* box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px; */
}
figure {
  width: 600px;
}
figure img {
  width: 100%;
}
.info {
  width: 600px;
}
.info p {
  margin-bottom: 20px;
}
.back {
  cursor: pointer;
  display: flex;
  gap: 0 10px;
  margin-bottom: 40px;
  border-radius: 6px;
  background: var(--background-color-secondary);
  width: max-content;
  padding: 5px 10px;
}
h1 {
  margin-bottom: 50px;
}
.upperInfo {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}
.lowerInfo {
  margin-top: 50px;
}
.back-arrow {
  width: 20px;
  height: 20px;
}

@media only screen and (max-width: 600px) {
  .main {
    padding: 40px 28px;
  }
  .container {
    flex-direction: column;
  }
  .back {
    box-shadow: 0px 0px 7px rgba(0, 0, 0, 0.293139);
    border-radius: 2px;
    width: 104px;
    margin-bottom: 64px;
    justify-content: center;
    padding: 6px;
    background: var(--background-color-secondary);
  }

  figure {
    max-width: 320px;
  }
  .info {
    width: 100%;
  }
  .upperInfo {
    display: block;
  }
}
</style>