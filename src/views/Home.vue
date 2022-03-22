<template>
  <SideMenu :isShow="isShowMenu" @close="setMenu" />
  <section class="landing">
    <header class="relative flex-sm-row flex-column align-items-sm-center align-items-end">
      <button class="build-project-button upperCase w-sm-25 w-100">
        <a href="#">start your project</a>
      </button>
      <button @click.prevent="setMenu" class="menu-button mt-4 mt-sm-0 ms-sm-4">
        <a href="#" class="icon-menu" />
      </button>
    </header>
    <div class="solgan">
      <h1>
        <a href="/" class="g-logo">DigiSalad</a>
      </h1>
      <div class="text">
        <p>WE CREATE</p>
        <p>AMAZING</p>
        <p>DIGITAL EXPERIECES</p>
      </div>
    </div>
    <div class="side-text d-none d-md-block">
      <p class="text">DIGITAL AGENCY</p>
    </div>
    <div class="dish-wrapper">
      <div class="dish-container">
        <span class="dish" />
        <p class="dish-text upperCase">taste us now</p>
      </div>
    </div>
  </section>

  <div class="about-wrapper px-4 px-md-6">
    <IntroductionBoard
      titleClass="about"
      :showButton="true"
      :title="about.title"
      :content="about.content"
      :buttonText="about.button"
    >
      <template v-slot:video>
        <div class="video-container video-ratio-4by3">
          <iframe
            title="DigiSalad - 為您創造驚喜的用戶體驗"
            frameborder="0"
            src="https://www.youtube.com/embed/IeIRJ9jZ5Ro"
          />
        </div>
      </template>
    </IntroductionBoard>
  </div>

  <div class="awards-wrapper gx-0 ms-3 ms-sm-5 row ps-5">
    <IntroductionBoard
      class="introductionBoard col-12 col-md-6 col-lg-4"
      titleClass="awards"
      :title="awards.title"
      :content="awards.content"
      :showButton="false"
    />
    <div class="award-pic-wrapper pt-md-5 row mb-auto col-md-6  col-12">
      <div class="award-img col-6" />
      <div class="award-img col-6" />
      <div class="award-img col-6" />
      <div class="award-img col-6" />
    </div>
  </div>

  <div class="ingardients-wrapper">
    <div class="bg" />
    <IntroductionBoard
      titleClass="ingardients"
      :title="ingardients.title"
      :content="ingardients.content"
      :buttonText="ingardients.button"
      btnColor=" #585880"
    />
    <ul class="ingardient-gird gx-0 row px-4 px-md-6">
      <li class="ingardient-gird-item col-6 col-md-4" v-for="(item, idx) in ingardientGrid" :key="`food-${idx}`">
        <div class="img-wrapper">
          <img :src="item.img" alt />
        </div>
        <h4 class="name">{{ item.name }}</h4>
        <p class="content">{{ item.content }}</p>
        <button>view more</button>
      </li>
    </ul>
    <span class="btn-view crossLine">VIEW MORE DIGISALAD’S INGRADIENTS</span>
  </div>

  <div class="founder-wrapper w-100 w-sm-90 w-md-80 w-lg-70 px-4 px-md-6 flex-column flex-sm-row">
    <div class="founder-profile w-sm-30 w-100">
      <img src="../assets/funder.png" alt />
      <h4 class="name letterAnimation" v-html="funderNameAnmation"></h4>
      <p class="title letterAnimation" v-html="funderTitleAnmation"></p>
    </div>
    <div class="founder-cotent ps-sm-5 w-sm-70 w-100">
      <img src="../assets/comma.png" alt />
      <p class="text">
        A great digital work isn’t about designing beautiful pages purely. It is about context - how do we deliver the
        <bold>right experience to the right person at the right time.</bold>The most important thing is that your work can engage customers at anytime, anywhere and let users experience an entire amazing digital journey.
      </p>
    </div>
  </div>
  <div class="brand-wrapper px-4 px-md-6">
    <IntroductionBoard
      titleClass="brands"
      :title="brand.title"
      :content="brand.content"
      :showButton="false"
    >
      <template v-slot:others>
        <img src="../assets/brands.png" alt />
      </template>>
    </IntroductionBoard>
  </div>

  <section class="moblie-wrapper flex-column flex-md-row p-5  p-md-8 p-lg-12">
    <span class="icon nex-btn">
      <img src="../assets/arrow-left.png" alt="">
    </span>
     <span class="icon prv-btn">
      <img src="../assets/arrow-right.png" alt="">
    </span>
    <div class="relative mb-3">
      <img src="../assets/LP_fb.png" class="LP-fb"/>
      <button
      class=" btn-view upperCase "
      >view project</button>
    </div>
    <div class="moblie-content p-0 p-sm-5 ps-md-5 ">
      <p class="subtitle">HIGHLIGHTED SHOWCASE</p>
      <h3 class="title crossLine">LP CLUB MOBILE APP</h3>
      <p
        class="context"
      >Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.</p>
    </div>

  </section>
</template>


<script setup>
import IntroductionBoard from '../components/IntroductionBoard.vue'
import SideMenu from '../components/SideMenu.vue'
import { onMounted, reactive, ref, toRefs, watch, nextTick } from 'vue'
import { gsap, Expo } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

const info = reactive({
  about: {
    title: 'about digisalad',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.',
    button: 'view more'
  },
  awards: {
    title: 'awards',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc.',
    button: null
  },
  ingardients: {
    title: 'our ingardients',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.',
    button: 'our service'
  },
  brand: {
    title: 'our brand experience',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.',
    button: null
  }
})
const { about, ingardients, brand, awards } = toRefs(info)
const ingardientGrid = reactive([
  {
    img: new URL('../assets/Frame.png', import.meta.url).href,
    name: 'UX Design',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: new URL('../assets/Frame(1).png', import.meta.url).href,
    name: 'UX Design',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: new URL('../assets/Frame(2).png', import.meta.url).href,
    name: 'website development',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: new URL('../assets/Frame(3).png', import.meta.url).href,
    name: 'mobile app development',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: new URL('../assets/Frame(4).png', import.meta.url).href,
    name: 'ecommerce',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: new URL('../assets/Frame(5).png', import.meta.url).href,
    name: 'customer loyalty',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: new URL('../assets/Frame(6).png', import.meta.url).href,
    name: 'digital transformation',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: new URL('../assets/Frame(7).png', import.meta.url).href,
    name: 'digital marketing',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: new URL('../assets/Frame(8).png', import.meta.url).href,
    name: 'BRANDING',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  }
])
const isShowMenu = ref(false)
const setMenu = () => {
  isShowMenu.value = !isShowMenu.value
  console.log(isShowMenu.value)
}
/* 特效部分 */
const funderNameAnmation = ref('Tony Ng'.replace(/([^\x00-\x80]|\w)/g, "<span class='letter'>$&</span>"))
const funderTitleAnmation = ref('Founder & Creative Director'.replace(/([^\x00-\x80]|\w)/g, "<span class='letter'>$&</span>"))

onMounted(() => {
  gsap.to(".dish-container", 1, {
    y: 10,
    duration: 800,
    overwrite: "auto", // very important
    repeat: -1, yoyo: true,
    ease: "animEase "
  }, 0)
  textAnimation()
})
const textAnimation = async () => {
    await nextTick
    const letters = document.querySelector('.founder-profile');
    const animationEl = letters.querySelectorAll('.letterAnimation span')
    console.log(animationEl)
    if(animationEl.length === 0 ) return
    const tl = gsap.timeline({paused: true});
    animationEl.forEach(element => {
      tl.to(element, {
      duration: 0.1,
      color: 'white',
      ease: 'power1.inOut',
      stagger: 0.02
      });
      ScrollTrigger.create({
        animation: tl,
        trigger: '.founder-wrapper',
        start: 'top +=200px',
        markers: true
      });
    });

}
</script>

<style scoped lang="scss">
@import '../assets/style/bootstrap/utilities';
$ue-width: 1440; /* ue图的宽度 */
@function px2rem($px) {
  @return calc($px / 20)* 1rem;
}


.landing {
  width: 100%;
  height: 100vh;
  position: relative;
  background: url(../assets/bg.png);
  .solgan {
    top: px2rem(181);
    margin-left: 16%;
    .text {
      color: #fff;
      font-weight: 700;
      font-size: px2rem(32);
      letter-spacing: 8px;
    }
  }
}

.bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: url(../assets/bg.png) center no-repeat;
}
header {
  display: flex;
  justify-content: flex-end;
  padding: px2rem(40);
  .build-project-button {
    padding: 12px;
    color: #fff;
    font-size: px2rem(16);
    border-radius: 25px;
    background: linear-gradient(90deg, #4ee5ea 3.94%, #26d0a8 94.73%);
  }
}
.icon-menu {
  display: block;
  width: 30px;
  height: 22px;
  background: url(../assets/icon-menu.png) 0 0 no-repeat;
}
.vertical-text {
  font-size: 1rem;
}
.side-text {
  position: absolute;
  left: px2rem(62.5);
  top: calc(50% - 19px / 2 - 97px);
  font-weight: 700;
  color: #fff;
  writing-mode: vertical-lr;
  .text {
    font-size: 16px;
    letter-spacing: 0;
  }
}
.side-text:after {
  content: "";
  position: absolute;
  left: calc(50% - 2px);
  bottom: -128px;
  margin-left: auto;
  display: block;
  height: 113px;
  width: 2px;
  background: #fff;
}
.about-wrapper {
  margin-bottom: 56px;
}
.dish-wrapper {
  position: absolute;
  margin-left: -37.5px;
  left: 50%;
  bottom: 56px;
}
.dish-wrapper::after {
  content: "";
  position: absolute;
  left: calc(50% - 2px);
  bottom: -100px;
  margin-left: auto;
  display: block;
  height: 86px;
  width: 2px;
  background: linear-gradient(180deg, #fff 50%, #808080 50%);
}
.dish {
  display: block;
  margin: auto;
  width: 65px;
  height: 65px;
  background: url(../assets/dish.png) center no-repeat;
  background-size: cover;
}
.dish-text {
  padding-top: 8px;
  font-size: px2rem(16);
  font-weight: 700;
  color: #fff;
}

.video-container {
  position: relative;
  width: 100%;
  height: 0;
  overflow: hidden;
  box-sizing: border-box;
}
.video-container iframe,
.video-container video {
  position: absolute;
  top: 0;
  left: 0;
  border: none;
  width: 100%;
  height: 100%;
}
.video-ratio-16by9 {
  padding-bottom: 56.25%; /* 9/16 */
}
.video-ratio-4by3 {
  padding-bottom: 75%; /* 3/4 */
}

.ingardients-wrapper {
  position: relative;
  color: #fff;
  text-align: center;
  .bg {
    z-index: -1;
    position: absolute;
    top: -10%;
    left: 0;
    width: 100%;
    height: calc(100% + 20%);
    border-radius: 32px;
    background: #26c6d0;
  }
  button {
    padding: 24px 35px;
    font-size: 14px;
    color: #fff;
    border: 2px solid #fff;
    border-radius: 30px;
  }
  .btn-view {
   padding-top: 96px;
   position: relative;
   display: inline-block;
   font-size: px2rem(24);
   font-weight: 700;
   letter-spacing: 2px;
  }
}
.crossLine::before {
  content: '';
  z-index: -1;
  position: absolute;
  bottom: 8px;
  left: 0;
  background: #FFBC58;
  width: 100%;
  height: 8px;
}
.ingardient-gird {
  box-sizing: border-box;
  position: relative;
  width: 100%;
  .ingardient-gird-item {
    padding-top: px2rem(60);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
  }
}

.ingardient-gird-item {
  .name {
    width: 142px;
    margin: 20px 0;
    font-size: 20px;
    font-weight: 700;
    text-align: center;
  }
  .content {
    margin-bottom: 20px;
    font-size: px2rem(18);
    line-height: 28px;
    text-align: center;
  }
  .img-wrapper {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 108px;
    height: 108px;
    border-radius: 50%;
    background: #fff;
  }
}
.founder-wrapper {
  margin-top: px2rem(96);
  padding: px2rem(96) px2rem(88);
  display: flex;
  border-radius: 0 32px 32px 32px;
  background-color: #fff;
  background: url("../assets/funder-bg.png.png") center no-repeat;
  background-size: cover;
}
.founder-profile {
  text-align: center;
  color: #262626;
  img {
    width: px2rem(204);
    height: px2rem(204);
    margin-bottom: 32px;
    border-radius: 50%;
  }
  .name {
    font-size: 20px;
    line-height: 24px;
    font-weight: 700;
    text-align: center;
  }
  .title {
    font-size: px2rem(16);
    font-style: italic;
    letter-spacing: 2px;
  }
}
.founder-cotent {
  text-align: center;
  color: #fff;
  img {
    margin-bottom: 16px;
  }
  .text {
    text-align: left;
    font-size: px2rem(22);
    line-height: px2rem(48);
    letter-spacing: 2px;
  }
}

.awards-wrapper {
  position: relative;
  top: 0;
  left: 0;
  padding-bottom: px2rem(88);
  background: #fff;
  border-radius: 32px 0 0 32px;
  img {
    object-fit: contain;
  }
}
.award-pic-wrapper {
  .award-img {
    width: px2rem(280);
    height: px2rem(104);
    background: url(../assets/award.png) center no-repeat;
  }
}

.brand-wrapper {
  background: #fff;
  img {
    display: inline-block;
    width: 100%;
  }
}
.moblie-wrapper {
  display: flex;
  width: 100%;
  background: url("../assets/app-bg.png") 0 0 no-repeat;
  background-size: cover;
}
.moblie-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  .LP-fb {
    width: px2rem(320);
    height: px2rem(320);
    border-radius: 24px;
  }
  .moblie-content {
    color: #fff;
  }
  .btn-view {
    padding: px2rem(30) px2rem(15);
    position: absolute;
    right: -10%;
    bottom: -10%;
    @include primaryBtn();
    font-size: px2rem(16);
  }
}
.moblie-wrapper {
  .icon {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 53px;
    height: 53px;
    border-radius: 50%;
    background: #26C6D0;
    img{
      height: 32px;
    }
  }
}
.moblie-content {
  flex: 1;
  .subtitle {
    font-size: px2rem(16);
  }
  .title {
    z-index: 999;
    position: relative;
    font-weight: 700;
    font-size: px2rem(32);
    line-height: 39px;
    letter-spacing: 3.63636px;

  }
  .context {
    font-size: px2rem(16);
  }
}
</style>
