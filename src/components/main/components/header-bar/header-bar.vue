<template>
  <div class="header-bar">
	  <span @click="handleClick"></span>	<!--获取store中router列表-->
    <sider-trigger :collapsed="collapsed" icon="md-menu" @on-change="handleCollpasedChange"></sider-trigger>
    <custom-bread-crumb show-icon style="margin-left: 30px;" :list="breadCrumbList"></custom-bread-crumb>
    <div class="custom-content-con">
      <slot></slot>
    </div>
  </div>
</template>
<script>
import siderTrigger from './sider-trigger'
import customBreadCrumb from './custom-bread-crumb'
import './header-bar.less'
export default {
  name: 'HeaderBar',
  components: {
    siderTrigger,
    customBreadCrumb
  },
  props: {
    collapsed: Boolean
  },
  computed: {
    breadCrumbList () {
      return this.$store.state.app.breadCrumbList
    },
	  getRList () {
    	return this.$store.state.app.rList
	  }
  },
  methods: {
    handleCollpasedChange (state) {
      this.$emit('on-coll-change', state)
    },
	  handleClick () {
    	console.log(this.getRList)
	  }
  }
}
</script>
