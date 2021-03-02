<template>
  <view style="width: 100%; height: 100%;">
    <view class="tabs">
      <view v-for="(tab, index) in tabs" class="tab-item" :class="current==index&&'active'" @click="current = index">
      {{tab.title}}
      </view>
    </view>
    <swiper :current="current" class="swiper-box" @change="onChange">
        <swiper-item v-for="(item ,index) in tabs" :key="index">
          <scroll-view scroll-y="true" style="height: 100%;" @scrolltolower="scrolltolower">
            <!-- #ifdef MP -->
            <slot name="{{'content' + index}}"></slot>    
            <!-- #endif -->
            <!-- #ifndef MP -->
            <slot :name="'content'+index"></slot>
            <!-- #endif -->
          </scroll-view>
        </swiper-item>
    </swiper>
  </view>
</template>

<script>
	export default {
    name: 'swiperTab',
    props: {
      currentTab: {
        type: Number,
        default: 0
      },
      tabs: {
        type: Array,
        default: []
      }
    },
		data() {
			return {
				current: this.currentTab
			};
		},
    methods: {
      onChange(e) {
        this.current = e.detail.current;
        this.$emit('change', e.detail.current);
      },
      scrolltolower(e) {
        this.$emit('onReachBottom', this.current);
        console.log(this.current)
      }
    }
	}
</script>
<style>
swiper-tab{
  display: block;
  height: 100%;
}
</style>
<style lang="scss" scoped>
.tabs{
  width: 750rpx;
  height: 75rpx;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  .tab-item {
    width: 20%;
    text-align: center;
    color: grey;
    line-height: 73rpx;
    font-size: 32rpx;
    font-weight: 500;
    height: 100%;
    box-sizing: border-box;
    &.active{
      color: #3ADAA2;
      border-bottom: 2rpx solid  #3ADAA2;
	    border-radius: 0 0 102% 100%/0 0 100% 100%;
    }
  }
}
.swiper-box{
  width: 100%;
  height: calc(100% - 75rpx);
  overflow: auto;
}
</style>
