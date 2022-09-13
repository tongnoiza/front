<template>
   
 
</template>
<script>
export default {
    name:'forminput',
    data(){
        return {
            form:{},
            valid:false,
            dialog: false,                   
        }
    },created() {
    this.$nuxt.$on('save',this.save())
  }
}
</script>
<style lang="">
    
</style>