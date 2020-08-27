<template>
  <div>
    <h1 style="text-align: center">Nuxt SSR - Countries</h1>
    <ul>
      <template v-for="country in countries">
        <hr :key="country.name" />
        <li :key="country.name">
          <NuxtLink :to="{ path: `country/${country.code}` }">
            {{ country.name }}
          </NuxtLink>
        </li>
      </template>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData() {
    const headers = {
      'x-rapidapi-host': 'wft-geo-db.p.rapidapi.com',
      'x-rapidapi-key': '339430d5bamsha7851291cba4fb8p1d4752jsn2a5fe48d0b2b',
      useQueryString: true,
    }
    const { data } = await axios.get(
      'https://wft-geo-db.p.rapidapi.com/v1/geo/countries',
      {
        headers,
      }
    )
    return { countries: data.data }
  },
}
</script>

<style scoped>
ul {
  padding: 100px;
  list-style-type: none;
}
li {
  padding: 20px;
  text-align: center;
}
</style>
