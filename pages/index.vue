<template>
  <div>
   
  <v-row justify="start" align="start"> 
    <v-col cols="12" sm="4" md="12">
   
    </v-col>
     </v-row>
   
 </div>
</template>

<script>
import CommentBox from '~/components/CommentBox.vue'
export default {
  components: { CommentBox },
  name: 'IndexPage',
  data:() => ({
    length: 3,
      onboarding: 0,
      send:[]
  }),
  activated(){
this.send = [
  {name:'tong',text:'dfjasjdfjaskdjfkaskkfd'},
  {name:'tonguuza',text:'dfjasjdfjaskdjfkaskkfd'},
  {name:'tongnoi',text:'dfjasjdfjaskdjfkaskkfd'},
  {name:'tongza',text:'dfjasjdfjaskdjfkaskkfd'},
  {name:'tong sontaya',text:'dfjasjdfjaskdjfkaskkfd'}
]
  },
  methods:{
 async   a(){
    
    },
    next () {
        this.onboarding = this.onboarding + 1 === this.length
          ? 0
          : this.onboarding + 1
      },
      prev (){
        this.onboarding = this.onboarding - 1 < 0
          ? this.length - 1
          : this.onboarding - 1
      }
  }
}
</script>
<style>
.main{
align-content: left;
}


</style>