<template>
  <div>
    <h1>{{ itemDetail.name }}</h1>
    <p>{{ itemDetail.code + itemDetail.id + itemDetail.parentId }}</p>
  </div>
</template>

<script>
import axios from "axios"

export default {
  name: "ItemDetail",
  async asyncData (context) {
    const { data } = await axios({
      method: "GET",
      url: "http://localhost:3000/dist.json"
    })

    const id = Number.parseInt(context.params.id)
    const itemDetail = data.posts.find(item => item.id === id)

    return {
      itemDetail
    }
  }
}
</script>

<style>

</style>