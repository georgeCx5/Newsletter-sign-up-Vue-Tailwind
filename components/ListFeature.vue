<script>
import iconList from '@/assets/images/icon-list.svg?url'
export default {
   data(){
      return{
         iconList,
      }
   },
   props: {
      feature: String,
   }
}
</script>
<template>
   <div class=" flex gap-4">
      <img :src="iconList" alt="iconList">
      <h4>{{ feature }}</h4>
   </div>
</template>