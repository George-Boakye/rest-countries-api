<template>
  <div class="home">
    <div class="inputs">
      <div class="search">
        <figure><img src="@/assets/search.svg" alt=""></figure>
        <input type="text" placeholder="Search for a country..." v-model="searchTerm" />
      </div>

      <div class="select">
        <select name="" id="" v-model="selectReg">
          <option value="">Filter by Region</option>
          <option :value="region" v-for="region in regions" :key="region">{{ region }}</option>
        </select>
      </div>

    </div>

    <div class="home_content">
      <Card :countries="filteredCountries"> </Card>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Card from '@/components/Card.vue'
import { mapActions, mapGetters } from "vuex";

export default {
  name: "HomeView",
  components: {
    Card,
  },
  data: () => ({
    searchTerm: "",
    selectReg: '',
    regions: [],
  }),
  async mounted() {
    await this.getAllCountries();
    this.getRegions();
  },
  computed: {
    ...mapGetters({
      countries: "getCountries",
    }),
    filteredCountries() {
      if (this.searchTerm) {
        return this.countries.filter((country) =>
          country.name.common.toLowerCase().includes(this.searchTerm.toLowerCase())
        );
      } else if (this.selectReg) {
        return this.countries.filter(country => country.region === this.selectReg)
      }
      else {
        return this.countries;
      }
    },
  },
  methods: {
    ...mapActions({
      getAllCountries: "getAllCountries",
    }),

    getRegions() {
      const allRegions = this.countries.map(country => country.region)
      const idealRegions = [...new Set(allRegions)]
      this.regions = idealRegions
    },
  },
}
</script>


<style scoped>
.home {
  padding: 40px 60px;
  background: var(--background-color-primary);
}

.search,
.select {
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
  width: 200px;
  height: 50px;
  text-align: center;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 5px;
  background: var(--background-color-secondary);
}

.search{
  width: 480px;
  justify-content: left;
  padding-left: 32px;
}

.inputs {
  display: flex;
  justify-content: space-between;
  background: var(--background-color-primary);

}

select,
input {
  padding: 10px;
  border: none;
  width: 250px;
  outline: none;
  background: var(--background-color-secondary);
  color: var(--text-primary-color);
}


@media only screen and (max-width: 600px) {
  .home{
    padding: 24px 16px;
  }
    .inputs{
      flex-direction: column;
      gap:  40px;
    }
    .search{
      width: 100%;
    }

    /* .home_content{
      padding: 0 56px;
    } */
}
</style>
