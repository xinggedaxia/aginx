<template>
  <el-autocomplete
    v-model="inputVal"
    :fetch-suggestions="querySearchAsync"
    :placeholder="placeholder"
    size="small"
    style="width: 260px"
    :suffix-icon="showIcon?'el-icon-search':''"
    v-bind="$attrs"
    @select="handleSelect"
  />
</template>

<script>
export default {
  name: 'RemoteSearch',
  props: {
    value: {
      type: String,
      default: ''
    },
    // 远程地址
    url: {
      type: String,
      default: '',
      require: true
    },
    showIcon: {
      type: Boolean,
      default: false
    },
    placeholder: {
      type: String,
      default: '请输入搜索内容'
    }
  },
  data() {
    return {
    }
  },
  computed: {
    inputVal: {
      get() {
        return this.value
      },
      set(value) {
        this.$emit('input', value)
      }
    }
  },
  mounted() {
    console.log(this.value)
  },
  methods: {
    handleSelect(item) {
      this.$emit('handleSelect', item)
    },
    querySearchAsync(queryString, cb) {
      if (queryString) {
        // 发送请求
        setTimeout((item, index) => {
          const data = [{ label: '启用', value: '启用' }, { label: '停用', value: '停用' }]
          cb(data)
        }, 500)
      } else {
        cb([])
      }
      // // 发送请求
      // var results = queryString ? restaurants.filter(this.createStateFilter(queryString)) : restaurants
      //
      // clearTimeout(this.timeout)
      // this.timeout = setTimeout(() => {
      //   cb(results)
      // }, 3000 * Math.random())
    },
    createStateFilter(queryString) {
      return (state) => {
        return (state.value.toLowerCase().indexOf(queryString.toLowerCase()) === 0)
      }
    }
  }
}
</script>

<style scoped>

</style>
