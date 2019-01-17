<template>
    <div class="cartcontrol">
    	<transition name="fade">
    		<div class="cart-decrease" v-show="food.count>0" @click="decreaseCart">
    		<transition name='inner'>
    			<span class="inner iconfont icon-jian"></span>
    		</transition>
    	</div>
    	</transition>
    	<div class="cart-count" v-show="food.count>0">{{food.count}}</div>
    	<div class="cart-add iconfont icon-jia" @click="addCart"></div>
    </div>
</template>
<script type="ecmascript-6">
import Vue from 'vue';
    export default {
    	props: {
    		food: {
    			type: Object
    		}
    	},
    	methods: {
    		decreaseCart(event) {
    			if (!event._constructed) {
    				return;
    			}
    			if (this.food.count) {
    				this.food.count--;
    			}
    		},
    		addCart(event) {
    			if (!event._constructed) {
    				return;
    			}
    			if (!this.food.count) {
    				Vue.set(this.food, 'count', 1);
    			} else {
    				this.food.count++;
    			}
    		}
    	}
    };
</script>
<style lang='stylus' rel="stylesheet/stylus">
    .cartcontrol
      font-size:0
      .cart-decrease,.cart-add
        display:inline-block
        padding:6px
        &.fade-enter-active,&.fade-leave-active
          transition:all 0.4s linear
          transform:rotate(0)
        &.fade-enter,&.fade-leave-active
          opacity:0
          transform:translate3d(24px,0,0)
          transform:rotate(-180deg)
        .inner
          display:inline-block
          font-size:24px
          line-height:24px
          color:rgb(0,160,220)
      .cart-count
        display:inline-block
        vertical-align:top
        width:12px
        padding-top:6px
        line-height:24px
        text-align:center
        font-size:10px
        color:rgb(147,153,159)
      .cart-add
        display:inline-block
        font-size:24px
        line-height:24px
        padding:6px
        color:rgb(0,160,220)
</style>
