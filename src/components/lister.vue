<template>
  <div v-for="hero in thisList" :key="hero.hero_name" class="hero">
    <img :src="'/images/' + hero.hero_img" />
  </div>
</template>

<script>
export default {
    methods:{
        async loadList(list){
            this.thisList = list 
        }
    },
    data(){
        return{
            thisList:[],
        }
    }
}
</script>

<style>

</style>