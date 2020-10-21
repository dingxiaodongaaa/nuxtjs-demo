<template>
  <div>
    <h1>{{ title }}</h1>
    <foo :posts="posts"></foo>
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
  // 当想要动态页面内容有利于 seo 或者是提升首屏渲染速度的时候，就在 asyncData 发请求拿数据
  async asyncData () {
    // 只能在页面组件中使用
    // 如果子组件中需要使用服务端渲染生成的动态数据，只能通过在页面组件中的 asyncData 中获取数据之后传给非页面子组件
    // asyncData 中没有 this，因为他是在组件初始化之前调用的
    const res = await axios({
      method: "GET",
      url: "http://localhost:3000/dist.json"
    })
    return res.data
  },
  // 如果是非异步数据或者是普通数据，则正常的初始化到 data 中即可
  data () {
    return {
      foo: "bar"
    }
  }
}
</script>

<style>

</style>