<template>
  <div>
    <h1 style="text-align: center">VUE SSR - Countries</h1>
    <v-container>
      <v-list three-line>
        <template v-for="(country, index) in countries">
          <v-divider :key="index"></v-divider>
          <v-list-item :key="country.name">
            <v-list-item-content>
              <v-list-item-title>
                <NuxtLink :to="{ path: `country/${country.code}` }">
                  {{ country.name }}
                </NuxtLink>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-container>
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
