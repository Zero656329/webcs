<template>
  <div>

    <h2>{{title}}</h2>
    <el-form>
      <el-form-item v-for="key in keys" v-bind:label="labels[key]" v-bind:key="key">
        <el-input v-model="items[key]"></el-input>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
  export default {
    computed: {
      keys() {
        return Object.keys(this.items)
      }
    },
    props: ['items', 'labels', 'title']
  }
</script>
