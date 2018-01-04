<template>
  <div>
    <h1>Search iTunes</h1>
    <br/>
    <form @submit.prevent="submit">
      <input
        type="text"
        placeholder="Enter Artist Name"
        v-model="search"
        />
    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      search: ''
    }
  },
  methods: {
    submit (e) {
      this.$router.push(`result/${this.search}`)
    }
  }
}
</script>

<style>
* {
  text-align: center;
}

h1 {
  padding: 20px;
}
</style>
