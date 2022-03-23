

<template>
  <section class=" info-board-wrapper">
    <div class="title-wrapper">
      <p class="title anim-typewriter" :class="titleClass"></p>
      <span class="dot" />
    </div>
      <slot name="video" />
    <p class="content">{{ content }}</p>

    <button class="btn-view" v-if="showButton">{{ buttonText }} <span class="line" />  </button>
    <slot name="others" />
  </section>
</template>
<script setup>
import { onMounted, ref, watch } from 'vue'

import { gsap, SteppedEase } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { TextPlugin } from 'gsap/TextPlugin'

gsap.registerPlugin(ScrollTrigger)
gsap.registerPlugin(TextPlugin)

onMounted(() => {
  titleAnimation()
})
const titleAnimation = () => {
  gsap.to('.' + titleClass, {
    text: {
      value: title
    },
    duration: 2,
    ease: SteppedEase.config(37),
    scrollTrigger: {
      trigger: '.' + titleClass, //觸發得物件
      start: "top +=500px", // (物件開始位置, 卷軸開始位置) top center bottom px
    }
  })
}
const props = defineProps({
  titleClass: {
    type: String,
    default: ''
  },
  title: String,
  content: String,
  showButton: {
    type: Boolean,
    default: true
  },
  buttonText: String,
  btnColor: {
    type: String,
    default: '#26c6d0'
  },
})
const { titleClass, title, btnColor } = props

</script>
<style scoped lang="scss">
@import '../assets/style/bootstrap/utilities';
$ue-width: 1440; /* ue图的宽度 */
@function px2rem($px) {
  @return calc($px / 20)* 1rem;
}

.info-board-wrapper {
  position: relative;
  text-align: center;
}
.title-wrapper {
  & .dot {
    display: inline-block;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: #ee6c8a;
  }
}
.title {
  position: relative;
  padding-top: 104px;
  padding-bottom: 10px;
  margin-bottom: 24px;
  display: inline-block;
  text-align: center;
  text-transform: uppercase;
  font-weight: 700;
  font-size: px2rem(28);
  line-height: 34px;
  letter-spacing: px2rem(2.4);
  color: #262626;
}
// .anim-typewriter {
//   width: 0;
// }

.title::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: 0px;
  width: 100%;
  height: 15px;
  background: url(../assets/wave.png) center 0 no-repeat;
}

.content {
  margin-top: 24px;
  font-size: px2rem(16);
  line-height: px2rem(28);
  /* or 175% */
  text-align: center;
  letter-spacing: 1px;
  color: #262626;
}

button {
  padding: 24px 40px;
  margin-top: 32px;
  @include primaryBtn( v-bind(btnColor))
}

.line {
  display: inline-block;
  height: 2px;
  width: 32px;
  vertical-align: middle;
  background: #fff;
}
</style>
