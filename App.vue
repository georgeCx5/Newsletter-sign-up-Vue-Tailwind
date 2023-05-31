<script>
import ListFeatureVue from './components/ListFeature.vue'

import signUpMobile from '@/assets/images/illustration-sign-up-mobile.svg?url'
import signUpDesktop from '@/assets/images/illustration-sign-up-desktop.svg?url'
import iconSuccess from '@/assets/images/icon-success.svg?url'

export default {
  data() {
    return {
      signUpMobile,
      signUpDesktop,
      iconSuccess,
      successForm: null,
      rgxEmail: new RegExp(/^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/),
      emailValue: '',
      hoverBtn: 'hover:bg-gradient-to-bl from-neo-first to-neo-second',
    }
  },
  components: {
    ListFeatureVue,
  },
  methods: {
    signUpEmail() {
      this.successForm = this.rgxEmail.test(this.emailValue);
      if (this.successForm) this.emailValue = '';
    },
    signOutEmail() {
      this.successForm = null;
    }
  },
  computed: {
    inputState() {
      if (this.successForm == false) {
        return 'bg-red-100 text-neo-tomato border-neo-tomato';
      } else {
        return 'border-neo-grey';
      }
    }
  }
}
</script>
<template>
  <body class=" flex flex-col dsk:justify-center items-center dsk:h-screen bg-neo-charcoal-grey">
    <main v-show="successForm == false || successForm == null"
      class=" flex flex-col dsk:flex-row-reverse gap-10 dsk:gap-16 dsk:py-6 pb-10 dsk:pl-12 dsk:pr-6 bg-neo-white font-roboto dsk:rounded-[36px]">
      <img class=" dsk:hidden" :src="signUpMobile" alt="signUpMobile">
      <img class=" hidden dsk:block" :src="signUpDesktop" alt="signUpDesktop">
      <div class=" flex flex-col dsk:justify-center gap-10 dsk:w-[376px] px-6 dsk:px-0">
        <div class=" flex flex-col gap-6 w-[327px] dsk:w-full text-neo-charcoal-grey">
          <h1 class=" text-[40px] dsk:text-[56px] leading-[40px] dsk:leading-[56px] font-bold">Stay updated!</h1>
          <p>Join 60,000+ product managers receiving monthly updates on:</p>
          <div class=" flex flex-col gap-[10px]">
            <ListFeatureVue feature="Product discovery and building what matters" />
            <ListFeatureVue feature="Measuring to ensure updates are a success" />
            <ListFeatureVue feature="And much more!" />
          </div>
        </div>
        <div class=" flex flex-col gap-6 w-[327px] dsk:w-full">
          <div class=" flex flex-col gap-2">
            <div class=" flex justify-between text-[12px] leading-[18px] font-bold">
              <h5 class=" text-neo-dark-slate-grey">Email address</h5>
              <h5 v-show="successForm == false" class=" text-neo-tomato">Valid email required</h5>
            </div>
            <input @keydown="successForm = null" class=" h-14 px-6 border rounded-lg" :class="`${inputState}`"
              type="email" placeholder="email@company.com" v-model="emailValue">
          </div>
          <button @click="signUpEmail()" class=" h-14 bg-neo-dark-slate-grey text-neo-white font-bold rounded-lg"
            :class="hoverBtn" type="submit">Subscribe to monthly
            newsletter</button>
        </div>
      </div>
    </main>
    <!-- Sign-up form end -->

    <!-- Success message start -->
    <main v-show="successForm"
      class=" flex flex-col gap-[263px] dsk:gap-10 w-[375px] dsk:w-[504px] dsk:h-[520px] pt-[149px] dsk:pt-12 pb-10 dsk:pb-16 px-6 dsk:px-16 bg-neo-white font-roboto dsk:rounded-[36px]">
      <div class=" flex flex-col items-start gap-10 ">
        <img :src="iconSuccess" alt="iconSuccess">
        <div class=" flex flex-col gap-6 text-neo-charcoal-grey">
          <h1 class=" text-[40px] dsk:text-[56px] leading-[40px] dsk:leading-[56px] font-bold">Thanks for subscribing!</h1>
          <p>
            A confirmation email has been sent to <span class=" font-bold">ash@loremcompany.com.</span>
            Please open it and click the button inside to confirm your subscription.
          </p>
        </div>
      </div>
      <button @click="signOutEmail()" class=" w-full h-14 bg-neo-dark-slate-grey text-neo-white font-bold rounded-lg"
        :class="hoverBtn">Dismiss
        message</button>
    </main>
  </body>
</template>