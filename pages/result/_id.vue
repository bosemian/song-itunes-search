<template>
  <div>
    <h1>Results for {{ $route.params.id }}</h1>
    <div v-if="albumExists">
      <div v-for="(album, i) in albumData" v-bind:key="i">
        <card
          :title="album.collectionCensoredName"
          :image="album.artworkUrl100"
          :artistName="album.artistName"
          :url="album.artistViewUrl"
          :color="picker(i)"
        />
      </div>
      {{ albumData }}
    </div>
    <div v-else>
      <h1>Could not find album</h1>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Card from '~/components/Card.vue'

export default {
  asyncData ({ params }) {
    return axios.get(`https://itunes.apple.com/search?term=${params.id}&entity=album`)
      .then((res) => {
        return { albumData: res.data.results }
      })
  },
  components: {
    Card
  },
  middleware: 'search',
  computed: {
    albumExists () {
      return this.albumData.length > 0
    }
  },
  methods: {
    picker (i) {
      return i % 2 == 0 ? 'red' : 'blue'
    }
  }
}
</script>

<style>

</style>
