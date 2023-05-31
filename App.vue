<script>
import ListFeatureVue from './components/ListFeature.vue'

import signUpMobile from '@/assets/images/illustration-sign-up-mobile.svg?url'
import signUpDesktop from '@/assets/images/illustration-sign-up-desktop.svg?url'
export default {
  data() {
    return {
      signUpMobile,
      signUpDesktop,
    }
  },
  components: {
    ListFeatureVue,
  }
}
</script>
<template>
  <body class=" font-roboto">
    <img :src="signUpMobile" alt="signUpMobile">
    <h1 class=" text-[40px] dsk:text-[56px] leading-[40px] dsk:leading-[56px] font-bold">Stay updated!</h1>

    Join 60,000+ product managers receiving monthly updates on:

    <ListFeatureVue feature="Product discovery and building what matters" />
    <ListFeatureVue feature="Measuring to ensure updates are a success" />
    <ListFeatureVue feature="And much more!" />

    <div class=" flex flex-col gap-6 w-[327px]">
      <div class=" flex flex-col gap-2">
        <div class=" flex justify-between">
          <h5>Email address</h5>
          <h5 class=" text-neo-tomato">Valid email required</h5>
        </div>
        <input class=" h-14 border border-neo-grey rounded-lg" type="email" placeholder="email@company.com">
      </div>
      <button type="submit">Subscribe to monthly newsletter</button>
    </div>

    <!-- Sign-up form end -->

    <!-- Success message start -->

    Thanks for subscribing!

    A confirmation email has been sent to ash@loremcompany.com.
    Please open it and click the button inside to confirm your subscription.

    Dismiss message

    <!-- Success message end -->
  </body>
</template>