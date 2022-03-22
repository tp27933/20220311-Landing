
<template>
  <nav class="menu" :class="{'active': isShow}" @touchmove.prevent.stop>
    <header>
      <h1>
        <a href="/" class="g-logo logo">DigiSalad</a>
      </h1>
      <span class="close" @click="emit('close')" />
    </header>

    <ul class="menu-grid-wrapper">
      <li class="menu-grid" v-for="(item, idx) in grid" :key="`menuu-grid-${idx}`">
        <div class="animation-wrapper">
            <div>
          <img :src="item.icon" alt />
        </div>
        <div>
          <p class="subtitle">{{ item.subTitle }}</p>
          <h4 class="title">{{ item.title }}</h4>
        </div>
        </div>
      </li>
    </ul>
  </nav>
</template>

<script setup>
import { onMounted, reactive, ref, watch } from 'vue'
import { gsap, Expo } from 'gsap'

const createImg = (src) => {
  return new URL(src, import.meta.url).href
}
const grid = reactive([
  {
    icon: createImg('../assets/Frame.png'),
    title: 'ABOUT US',
    subTitle: 'EMPOWERING BRANDS',
  },
  {
    icon: createImg('../assets/Frame(9).png'),
    title: 'SERVICES',
    subTitle: 'AREAS OF EXPERTISE'
  },
  {
    icon: createImg('../assets/Frame(1).png'),
    title: 'WORKS',
    subTitle: 'CASE STUDIES'
  },
  {
    icon: null,
    title: 'CONTACT',
    subTitle: 'START YOUR JOURNEY WITH US'
  },
  {
    icon: createImg('../assets/Frame(2).png'),
    title: 'CAREERS',
    subTitle: 'BE COOL WITH US'
  },
    {
    icon: createImg('../assets/Frame(3).png'),
    title: 'INSIGHTS',
    subTitle: 'OUR STRATEGIES'
  }
])
onMounted(()=>{
   gsap.set('.menu', {width: 0});
})
const props = defineProps({
  isShow: Boolean
}, { immediate: true })
const emit = defineEmits(['close'])
/*--頁面展開動畫--*/

watch(props, (prop) => {
  if (prop.isShow) {
    gsap.to('.menu', 0.3, {width: '100vw'});
    textAnimation()
    document.body.style.overflow = 'hidden';
    //document.addEventListener("touchmove", m, { passive: false });//禁止页面滑动
  } else {
    //開啟頁面滾動
  textAnimation(true)
  gsap.to('.menu', 0.5, {width: 0,   delay: 0.3});

    document.body.style.overflow = '';//出現滾動條
  }
})
const leftAnimationArr = reactive([])
const rightAnimationArr = reactive([])

const textAnimation = (reverse) => {
  // .menu-grid:nth-of-type(odd) .animation-wrapper'
  const leftElements = document.querySelectorAll('.menu-grid:nth-of-type(odd) .animation-wrapper')
  const rightElements = document.querySelectorAll('.menu-grid:nth-of-type(even) .animation-wrapper')
    console.log(gsap.utils.toArray('.menu-grid:nth-of-type(odd) .animation-wrapper'))
  if(reverse) {
    console.log(leftAnimationArr)
    leftAnimationArr.forEach((el,idx)=>{
      el.reverse();
    })
    rightAnimationArr.forEach((el,idx)=>{
      el.reverse();
    })
    return
  }

  leftAnimationArr.length = 0
  rightAnimationArr.length = 0
  leftElements.forEach((el,idx)=> {
    const animation= gsap.to(el, 0.5, {
      delay: 0.2* idx,
      left: 0,
       ease: Expo.in,
    });
    leftAnimationArr.push(animation)
  })
  rightElements.forEach((el,idx)=>{
    const animation = gsap.to(el, 0.5, {
      delay: 0.2*idx,
      right: 0,
       ease: Expo.in,
    });
    rightAnimationArr.push(animation)
  })
}
</script>

<style scoped lang="scss">
@function px2rem($px) {
  @return calc($px / 20)* 1rem;
}

.menu {
  z-index: 999;
  position: absolute;
  top: 0;
  right: 0;
  display: flex;
  flex-direction: column;
  height: 100vh;
  background: url(../assets/bg.png);
  overflow: hidden;
}

// .menu-grid-wrapper {
//   padding: 0 px2rem(80);
//   position: relative;
//   display: grid;
//   grid-template-columns: 1.5fr 1fr 1.5fr;
//   grid-template-rows: repeat(13, 1fr);
//   grid-gap: 20px;
//   height: calc(90% - 48px);
//   color: #fff;
// }

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: px2rem(24) px2rem(32);
}
.menu-grid-wrapper {
  flex:1;
}
.animation-wrapper{
  position: relative;
}
.menu-grid:nth-child(1),
.menu-grid:nth-child(3) {
  position: relative;
  grid-column-start: 1;
  grid-column-end: 2;
  .animation-wrapper {
    left: -100vw
  }
}
.menu-grid:nth-child(5){
    .animation-wrapper {
    left: -100vw
  }
}
.menu-grid:nth-child(1) {
  grid-row-start: 2;
  grid-row-end: 6;
  justify-content: center;
  align-items: center;
  background: url("../assets/menu-1.png") center no-repeat;
  background-size: cover;
  .dot {
    background: #ee6c8a;
  }
}
.menu-grid:nth-child(3) {
  grid-row-start: 6;
  grid-row-end: 11;
  justify-content: flex-start;
  align-items: flex-end;
  background: url("../assets/menu-4.png") center no-repeat;
  background-size: cover;
  .dot {
    background: #ee6c8a;
  }
}
.menu-grid:nth-child(2),
.menu-grid:nth-child(4) {
  position: relative;
  grid-column-start: 3;
  grid-column-end: 4;
  .animation-wrapper {
    right: -100vw
  }
}
.menu-grid:nth-child(6) {
   .animation-wrapper {
    right: -100vw
  }
}
.menu-grid:nth-child(2) {
  grid-row-start: 2;
  grid-row-end: 7;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-start;
  background: url("../assets/menu-3.png") center no-repeat;
  background-size: cover;
  .dot {
    background: #ee6c8a;
  }
}
.menu-grid:nth-child(4) {
  grid-row-start: 7;
  grid-row-end: 11;
  justify-content: center;
  align-items: center;
  background: url("../assets/menu-6.png") center no-repeat;
  background-size: cover;
  .dot {
    background: #ee6c8a;
  }
  .subtitle {
    color: #262626;
  }
  .title {
    color: #26c6d0;
  }
}
.menu-grid:nth-child(5),
.menu-grid:nth-child(6) {
  grid-column-start: 2;
  grid-column-end: 3;
}
.menu-grid:nth-child(5) {
  grid-row-start: 1;
  grid-row-end: 8;
  flex-direction: column;
  justify-content: flex-end;
  align-items: flex-start;
  background: url("../assets/menu-2.png") center no-repeat;
  background-size: cover;
  .dot {
    background: #ee6c8a;
  }
}
.menu-grid:nth-child(6) {
  grid-row-start: 8;
  grid-row-end: 13;
  justify-content: flex-start;
  align-items: flex-end;
  background: url("../assets/menu-5.png") center no-repeat;
  background-size: cover;
  .dot {
    background: #ee6c8a;
  }
}
.menu-grid {
  display: flex;
  padding:  px2rem(28)  px2rem(12);;
  border-radius: 15px;
}
.menu-grid .animation-wrapper {
   display: flex;
    .title {
    font-weight: 700;
    font-size: px2rem(24);
    line-height: 19px;
  }
  .subtitle {
    margin-bottom: 9px;
    font-size:  px2rem(16);
    line-height: 19px;
    letter-spacing: 1.8px;
  }
}
.menu::before {
  content: "";
  z-index: 0;
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(180deg, #585880 3.61%, #26c6d0 95.7%);
  opacity: 0.9;
}
.close {
  width: 24px;
  height: 24px;
}
.close::before,
.close::after {
  content: "";
  position: absolute;
  width: 3px;
  height: 24px;
  background: #fff;
  border-radius: 5px;
}
.close::before {
  transform: rotate(-45deg);
}
.close::after {
  transform: rotate(45deg);
}
.logo {
  padding-top:  px2rem(56);
  background-size: contain;
}
</style>
