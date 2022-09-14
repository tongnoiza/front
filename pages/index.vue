<template>
  <div>
  <v-row justify="start" align="start"> 
    <v-col sm="12" md="12">
      <v-data-table
    :headers="headtable"
    :items="AllUser.data"
    class="elevation-1"
    dense
  >
  <template v-slot:[`item.btn`]="{ item }">
      <v-row justify="center"> 
          <v-col md="8">    <v-btn color="primary" dense text @click="$nuxt.$emit('view','view',item.user_id)"><v-icon>mdi-account-eye</v-icon> </v-btn>
      <v-btn color="green" dense text @click="log(item.user_id)"><v-icon>mdi-account-plus-outline</v-icon> </v-btn>
      <v-btn color="red" dense text @click="log(item.user_id)"><v-icon>mdi-file-document-remove-outline</v-icon> </v-btn></v-col>
    </v-row>
    </template>
  </v-data-table>
    </v-col>
     </v-row>
   
 </div>
</template>

<script>
import CommentBox from '~/components/CommentBox.vue'
export default {
  components: { CommentBox },
  layout:'default',
  name: 'IndexPage',
 async fetch(){
   this.AllUser = await this.$axios.$get('http://yamq.dyndns.org:3002/getAllUsers')
  },
  data(){return {
    length: 3,
      onboarding: 0,
      send:[],
      AllUser:[],
      headtable:[{
          text: 'ชื่อ',
          align: 'start',
          value: 'user_firstname',
        },
        { text: 'นามสกุล', value: 'user_lastname' },
        { text: 'ชื่อกลาง', value: 'user_middlename' },
        { text: 'รหัสผ่าน', value: 'user_password' },
        { text: 'โหมด', align: 'center',value: 'btn' },]
  }}  ,
  activated(){

  },computed:{},
  methods:{
    log(n){
      console.log('pressed ',n)
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