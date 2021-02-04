<template>
  <div class="overview" @click="handleClick(articleData.id)">
    <div class="meta">
      <span class="item">{{ articleData.author }}</span>
      <span class="item">{{ articleData.time }}</span>
      <span class="item">{{ articleData.tag }}</span>
    </div>
    <h1 class="title">
      {{ articleData.title }}
    </h1>
    <div class="action">
      <el-button
        :style="{color: articleData.currentLike?'#6cbd45':''}"
        :icon="articleData.currentLike?'custom-icon-liked':'custom-icon-like'"
        size="mini"
      >
        100
      </el-button>
      <el-button icon="el-icon-chat-line-round" size="mini">100</el-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ArticleOverview',
  props: {
    articleData: {
      type: Object,
      default: () => ({}),
      require: true
    }
  },
  methods: {
    handleClick(id) {
      this.$message('in progress' + id)
    }
  }
}
</script>
<style lang="scss" scoped>
.overview {
  cursor: pointer;
  height: 140px;
  padding: 25px;
  border-bottom: 1px solid hsla(0, 0%, 59.2%, .2);

  .meta {
    display: flex;
    vertical-align: center;

    .item {
      position: relative;
      margin-right: 16px;
      font-size: 14px;
      color: #909090;
    }

    .item:not(:last-child):after {
      content: '';
      position: absolute;
      top: 7px;
      right: -9px;
      width: 2px;
      height: 2px;
      background-color: #b2bac2;
      border-radius: 50%;

    }
  }

  .title {
    margin: .5rem 0 1rem;
    font-weight: 600;
    line-height: 1.2;
    color: #2e3135;
  }

  .action {
    display: flex;

    ::v-deep {
      .el-button {
        height: 32px;
        border-radius: 0;
        font-size: 14px;
        outline: none;
      }

      .el-button + .el-button {
        margin-left: -1px;
      }

    }
  }
}
</style>
