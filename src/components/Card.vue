<template>
  <div class="container">
    <div
      class="card"
      v-for="country in countries"
      :key="country.name.common"
      @click="
        this.$router.push({
          name: 'singleCountry',
          params: { name: country.name.common },
        })
      "
    >
      <figure>
        <img :src="country.flags.png" alt="" />
      </figure>
      <div class="info">
        <h3>{{ country.name.common }}</h3>
        <p><strong>Population</strong>: {{ country.population }}</p>
        <p><strong>Region</strong>: {{ country.region }}</p>
        <p class="card-text-capital" v-if="country.capital">
          <strong>Capital</strong>:
          <span v-for="(capital, index) in country.capital" :key="index">{{
            capital
          }}</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    countries: {
      type: Array,
    },
  },
};
</script>

<style scoped >
h3 {
  font-weight: 800;
  font-size: 18px;
  line-height: 26px;
  color:var(--text-primary-color);
  margin-bottom: 16px;
}

.card {
  cursor: pointer;
  max-width: 264px;
  height: 300px;
  display: flex;
  flex-direction: column;
  box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px,
    rgba(60, 64, 67, 0.15) 0px 2px 6px 2px;
  border-radius: 5px;
  background: var(--background-color-secondary);
  color: var(--text-primary-color);
}

.info {
  margin: 20px;
  margin-top: 20px;
}

.card figure {
  margin: 0 auto;
  width: 100%;
  height: 120px;
}

.card img {
  width: 100%;
  height: 100%;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
}

.container {
  padding-top: 40px;
  display: grid;
  justify-content: center;
  grid-template-columns: repeat(4, max-content);
  gap: 75px;
  background: var(--background-color-primary);
}

@media only screen and (max-width: 600px) {
  .container {
    grid-template-columns: repeat(1, max-content);
  }
}
</style>
