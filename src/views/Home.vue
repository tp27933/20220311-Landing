<template>
  <SideMenu :isShow="isShowMenu" @close="setMenu" />
  <nav class="sticky-nav sticky-top bg-light">
    <h1 class="mb-0">
      <a href="/" class="g-logo colorful">DigiSalad</a>
    </h1>
    <div class="btns-group-warpper">
      <button class="build-project-button upperCase">
        <a href="#">start your project</a>
      </button>
      <button @click.prevent="setMenu" class="menu-button">
        <a href="#" class="icon-menu dark" />
      </button>
    </div>
  </nav>
  <section class="landing">
    <header class="relative px-4 pt-4 pb-12 align-items-center justify-content-between justify-content-sm-end">
      <button class="build-project-button upperCase ">
        <a href="#">start your project</a>
      </button>
      <button @click.prevent="setMenu" class="menu-button ms-sm-6">
        <a href="#" class="icon-menu light" />
      </button>
    </header>
    <div class="solgan">
      <div class="minHeight-container">
         <h1 >
        <a href="/" class="g-logo">DigiSalad</a>
      </h1>
      </div>

      <div class="text">
        <p>WE CREATE</p>
        <div  class="hightline">
          <div><p class="upperCase">amazing</p></div>
          <div><p class="upperCase">wonderful</p></div>
          <div><p class="upperCase">professional</p></div>
        </div>
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

  <div class="about-wrapper px-4 px-md-8 px-lg-main mx-lg-11">
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

  <div class="awards-wrapper px-4 ps-md-6 gx-0 ms-md-8 ms-lg-main row">
    <IntroductionBoard
      class="introductionBoard col-12 col-md-6 col-lg-4"
      titleClass="awards"
      :title="awards.title"
      :content="awards.content"
      :showButton="false"
    />
    <div class="award-pic-wrapper mt-auto  ps-sm-6 row col-12 col-md-6 col-lg-8 pe-md-2 pe-lg-main">
      <div class="award-img col-12 col-md-6" />
      <div class="award-img col-12 col-md-6" />
      <div class="award-img col-12 col-md-6" />
      <div class="award-img col-12 col-md-6" />
    </div>
  </div>

  <div class="ingardients-wrapper">
    <div class="bg" />
    <IntroductionBoard
      class="px-4 px-md-8 px-lg-main mx-lg-11"
      titleClass="ingardients"
      :title="ingardients.title"
      :content="ingardients.content"
      :buttonText="ingardients.button"
      btnColor=" #585880"
    />
    <div class="mx-md-8 mx-lg-main">
      <ul class="ingardient-gird gx-4 row px-4 px-md-6 ">
        <li class="ingardient-gird-item col-6 col-md-4" v-for="(item, idx) in ingardientGrid" :key="`food-${idx}`">
          <div class="img-wrapper" @mouseenter="bounceEnter">
            <img :src="item.img" alt />
          </div>
          <h4 class="name">{{ item.name }}</h4>
          <p class="content">{{ item.content }}</p>
          <button>view more</button>
        </li>
      </ul>
    </div>

    <span class="btn-view crossLine">VIEW MORE DIGISALAD’S INGRADIENTS</span>
  </div>
 <!-- w-100 w-sm-90 w-md-80 w-lg-70 -->
  <div class="pe-0 bg-light ps-md-0 pe-md-6">
    <div class="founder-wrapper  flex-column flex-sm-row ps-md-6 gx-0 me-md-8 me-lg-main px-4 pe-md-6">
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

  </div>
  <div class="brand-wrapper px-4 px-md-6">
    <IntroductionBoard
      class="px-4 px-md-8 px-lg-main mx-lg-11"
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

  <section class="moblie-wrapper flex-column flex-md-row p-5 px-4  p-md-8 p-lg-main">
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
      >view project  <span class="line" /></button>
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
import { gsap, Bounce, Power2 } from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { Flip } from 'gsap/Flip'
gsap.registerPlugin(ScrollTrigger)
gsap.registerPlugin(Flip);

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
    img: '/src/assets/Frame.png',
    name: 'UX Design',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: '/src/assets/Frame(1).png',
    name: 'UX Design',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: '/src/assets/Frame(2).png',
    name: 'website development',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: '/src/assets/Frame(3).png',
    name: 'mobile app development',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: '/src/assets/Frame(4).png',
    name: 'ecommerce',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: '/src/assets/Frame(5).png',
    name: 'customer loyalty',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: '/src/assets/Frame(6).png',
    name: 'digital transformation',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: '/src/assets/Frame(7).png',
    name: 'digital marketing',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  },
  {
    img: '/src/assets/Frame(8).png',
    name: 'BRANDING',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.'
  }
])
const isShowMenu = ref(false)
const setMenu = () => {
  logoAnimation()
  isShowMenu.value = !isShowMenu.value
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
  stickyNavAnimation()
})
/* landning text animation */
function bounceEnter(elClass) {
  const el = elClass.target.children[0]
  gsap.to(el, 1 / 4, {y:-40, ease:Power2.easeOut});
  gsap.to(el, 1 / 2, {y:0, ease:Bounce.easeOut, delay:1 / 4});
}
const logoAnimation = () => {
 const el =  document.querySelector('.solgan h1')
 let state = Flip.getState(el);
 el.classList.toggle('toggleLogo')
  Flip.from(state, {
    absolute: true, // uses position: absolute during the flip to work around flexbox challenges
    duration: 0.5,
    stagger: 0.1,
    ease: "back.in(0.8)"
  })
}

const textAnimation = async () => {
    await nextTick
    const letters = document.querySelector('.founder-profile');
    const animationEl = letters.querySelectorAll('.letterAnimation span')
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
      });
    });
}
/*  sticky nav animation */
const stickyNavAnimation = () => {
  // gsap.set('.sticky-nav',{ autoAlpha:0 })
  gsap.to('.sticky-nav', {
    display: 'flex',
    height: 80,
    duration: 5,
    opacity:1,
    ease: "power3",
    scrollTrigger: {
      trigger: ".about-wrapper",
      scrub: 0.3 ,
      markers: true,
      start: "top top",
      end: "bottom bottom",
    }
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
    margin-left: 16%;
    .text p{
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
}
.build-project-button {
  padding: 12px;
  color: #fff;
  font-size: px2rem(16);
  border-radius: 25px;
  background: linear-gradient(90deg, #4ee5ea 3.94%, #26d0a8 94.73%);
}
.sticky-nav {
  display: none;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;
  height: 0;
  opacity: 0;
  overflow: hidden;
  a {
    width: px2rem(120)
  }
  .icon-menu {
    width: 2rem;
  }
  .btns-group-warpper {
    display: flex;
  }
}
.minHeight-container {
  min-height: 80px;
}
.solgan {
  h1 {
    position: relative;
    z-index: 9999;
  }
}
.solgan .toggleLogo {
  position: absolute;
  z-index: 9999;
  top: 1.2rem;
  left: 1.6rem;
  transform: scale(0.6);
}
.solgan {
 .hightline {
    display: inline-block;
    height: 50px;
    // line-height: 48px;
    overflow: hidden;
    div {
      background: #26C6D0;
    }
    div:first-child {
      animation: show 5s linear infinite;
    }
    p {
      padding:4px 12px;
      height:45px;
      margin-bottom:45px;
    }
    div:nth-child(2) {
      background: #FFBC58;
    }
    div:nth-child(3) {
      background: #DC143C;
    }
 }
}

@keyframes show {
  0% {margin-top:-270px;}
  5% {margin-top:-180px;}
  33% {margin-top:-180px;}
  38% {margin-top:-90px;}
  66% {margin-top:-90px;}
  71% {margin-top:0px;}
  99.99% {margin-top:0px;}
  100% {margin-top:-270px;}
}


.icon-menu {
  display: block;
  width: 30px;
  height: 22px;

}
.icon-menu.dark {
background: url(../assets/icon-menu-dark.png) center no-repeat;
}
.icon-menu.light {
  background: url(../assets/icon-menu.png) center no-repeat;
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
    z-index: 0;
    position: absolute;
    top: -10%;
    left: 0;
    width: 100%;
    height: calc(100% + 20%);
    border-radius: 32px;
    background: #26c6d0;
  }
  button {
    padding: 21px 35px;
    font-size: px2rem(18);
    color: #fff;
    border: 2px solid #fff;
    border-radius: 50px;
  }
  .btn-view {
   padding-top: 96px;
   position: relative;
   display: inline-block;
   font-size: px2rem(24);
   font-weight: 700;
   letter-spacing: 2px;
  }
  ::v-deep(.ingardients) {
    color: #fff;
  }
  ::v-deep(.title::after) {
    background: url(../assets/wave2.png) center 0 no-repeat;
  }
}
.crossLine::after {
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
  position: relative;
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
    bold {
      color: #FFBC58;
    }
  }
}

.awards-wrapper {
  z-index: 999;
  position: relative;
  top: 0;
  left: 0;
  padding-bottom: px2rem(88);
  background: #fff;
  border-radius: 32px 0 0 32px;
  ::v-deep(.title-wrapper) {
    text-align: left;
  }
}
.award-pic-wrapper {
  .award-img{
    position: relative;
    overflow: hidden;
    background: url(../assets/award.png) center no-repeat;
    background-size: contain;
	&:before{
		content: "";
		display: block;
		padding-top: 50%;
	}
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
    .line {
      display: inline-block;
      height: 2px;
      width: 32px;
      vertical-align: middle;
      background: #fff;
    }
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
    display: inline-block;
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
