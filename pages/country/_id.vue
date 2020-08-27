<template>
  <div>
    <h1 style="padding: 20px">{{ country.name }}</h1>
    <img class="flag" :src="country.flagImageUri" alt="image not loaded" />
    <h1>{{ text }}</h1>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData({ params }) {
    const headers = {
      'x-rapidapi-host': 'wft-geo-db.p.rapidapi.com',
      'x-rapidapi-key': '339430d5bamsha7851291cba4fb8p1d4752jsn2a5fe48d0b2b',
      useQueryString: true,
    }
    const url = `https://wft-geo-db.p.rapidapi.com/v1/geo/countries/${params.id}`
    const { data } = await axios.get(url, {
      headers,
    })
    return { country: data.data, text: '' }
  },
}
</script>

<style scoped>
.flag {
  width: 50%;
}
</style>
