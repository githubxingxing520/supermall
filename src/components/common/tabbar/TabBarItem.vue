<template>
  <div class="tabbar_item"
       @click="handleItemClick">
    <div v-if="!isActive">
      <slot name="item-icon"></slot>
    </div>
    <div v-else>
      <slot name="item-icon-active"></slot>
    </div>
    <div :style="styleColor">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    activeColor: {
      type: String,
      default: "red"
    },
    path: {
      type: String,
      default: ""
    }
  },
  data () {
    return {

    };
  },
  computed: {
    isActive () {
      return this.$route.path.indexOf(this.path) !== -1
    },
    styleColor () {
      return this.isActive ? { color: this.activeColor } : {}
    }
  },
  watch: {

  },
  methods: {
    // 点击tab-item
    handleItemClick () {
      this.$router.replace(this.path)
    }
  }
};
</script>
<style lang="less" scoped>
.tabbar_item {
  flex: 1;
  text-align: center;
  height: 49px;
  font-size: 14px;
  img {
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
    margin-bottom: 2px;
  }
  .active {
    color: red;
  }
}
</style>
