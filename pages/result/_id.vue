<template>
  <div>
    <h1>Hello From result {{$route.params.id}}</h1>
    {{ albumData }}
  </div>
</template>

<script>
import axios from 'axios'
export default {
  asyncData ({ params }) {
    return axios.get(`https://itunes.apple.com/search?term=${params.id}&entity=album`)
      .then((res) => {
        console.log(res.data.results)
        return { albumData: res.data.results }
      })
  },
  middleware: 'search'
}
</script>

<style>

</style>
