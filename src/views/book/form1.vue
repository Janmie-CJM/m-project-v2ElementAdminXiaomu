<template>
  <div>
    <el-radio v-model="radio" label="1" @change="onchange($event,'陈间美')">备选项</el-radio>
    <el-radio v-model="radio" label="2" @change="onchange($event,'待遇送')">备选项</el-radio>

    <el-input v-model="input" placeholder="请输入密码" show-password type="textarea" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      radio: '1',
      ddddd: '1',
      input: ''
    }
  },
  methods: {
    onchange(label, name) {
      console.log(label, name)
    }
  }
}
</script>

<style lang="stylus" scoped>

</style>
