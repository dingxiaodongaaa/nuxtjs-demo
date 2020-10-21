<template>
  <div>
    <h1>Foo 组件</h1>
    <ul>
      <li v-for="item in posts" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'FooComponent',
  props: ["posts"]
}
</script>

<style>

</style>