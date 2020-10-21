<template>
  <div>
    <h1>Hello Nuxt.js!</h1>
    <foo :posts="posts" />
  </div>
</template>

<script>
import axios from "axios"
import Foo from "@/components/Foo"

export default {
  name: "HomePage",
  components: {
    Foo
  },
  async asyncData () {
    const { data } = await axios({
      method: "GET",
      url: "http://localhost:3000/dist.json"
    })
    return data
  }
}
</script>

<style>

</style>