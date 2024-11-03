<template>
    <view class="content">
        <uni-swiper-dot class="uni-swiper-dot-box" @clickItem=clickItem :info="info" :current="current" :mode="mode"
            :dots-styles="dotsStyles" field="content">
            <swiper class="swiper-box" @change="change" :current="swiperDotIndex">
                <swiper-item v-for="(item, index) in info.length" :key="index">
                    <view class="swiper-item" :class="'swiper-item' + index">
                        <text style="color: #fff; font-size: 32px;">{{ index + 1 }}</text>
                    </view>
                </swiper-item>
            </swiper>
        </uni-swiper-dot>

    </view>
</template>

<script setup lang="ts">
import { ref, PropType } from 'vue'
import { InfoListItem } from './index.d'
import { UniSwiperDotMode, UniSwiperDotDotsStyles } from '@uni-helper/uni-ui-types/index';

const props = defineProps({
    info: {
        type: Array<InfoListItem>,
        default: () => []
    },
    dotsStyles: {
        type: Object as PropType<UniSwiperDotDotsStyles>,
    },
    mode: {
        type: Object as PropType<UniSwiperDotMode>,
    }
})
const emits = defineEmits(['clickSwiperItem'])
const current = ref(0)
const swiperDotIndex = ref(0)
// 鼠标
const change = (e: any) => {
    current.value = e.detail.current
}
const clickItem = (e: number) => {
    swiperDotIndex.value = e
}
</script>

<style lang="scss">
.swiper-box {
    height: 200px;
}

.swiper-item {
    /* #ifndef APP-NVUE */
    display: flex;
    /* #endif */
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 200px;
    color: #fff;
}

.swiper-item0 {
    background-color: #cee1fd;
}

.swiper-item1 {
    background-color: #b2cef7;
}

.swiper-item2 {
    background-color: #cee1fd;
}

.image {
    width: 750rpx;
}

/* #ifndef APP-NVUE */
::v-deep .image img {
    -webkit-user-drag: none;
    -khtml-user-drag: none;
    -moz-user-drag: none;
    -o-user-drag: none;
    user-drag: none;
}

/* #endif */

@media screen and (min-width: 500px) {
    .uni-swiper-dot-box {
        width: 400px;
        margin: 0 auto;
        margin-top: 8px;
    }

    .image {
        width: 100%;
    }
}

.uni-bg-red {
    background-color: #ff5a5f;
}

.uni-bg-green {
    background-color: #09bb07;
}

.uni-bg-blue {
    background-color: #007aff;
}

.example-body {
    /* #ifndef APP-NVUE */
    display: flex;
    /* #endif */
    flex-direction: row;
    padding: 20rpx;
}

.example-body-item {

    flex-direction: row;
    justify-content: center;
    align-items: center;
    margin: 15rpx;
    padding: 15rpx;
    height: 60rpx;
    /* #ifndef APP-NVUE */
    display: flex;
    padding: 0 15rpx;
    /* #endif */
    flex: 1;
    border-color: #e5e5e5;
    border-style: solid;
    border-width: 1px;
    border-radius: 5px;
}

.example-body-item-text {
    font-size: 28rpx;
    color: #333;
}

.example-body-dots {
    width: 16rpx;
    height: 16rpx;
    border-radius: 50px;
    background-color: #333333;
    margin-left: 10rpx;
}

.active {
    border-style: solid;
    border-color: #007aff;
    border-width: 1px;
}
</style>