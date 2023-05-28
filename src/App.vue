<template>
  <div class="set-wrap">
    <div class="hero-set">
      <div v-for="hero in legion_agi" :key="hero.hero_name" class="hero">
        <img v-if="!hero.original_img" :src="'/images/' + hero.hero_img" />
        <img og v-if="hero.original_img" :src="'/images/' + hero.original_img" />

      </div>
    </div>
    <div class="hero-set">
      <div v-for="hero in hellbourne_agi" :key="hero.hero_name" class="hero">
        <img v-if="!hero.original_img" :src="'/images/' + hero.hero_img" />
        <img og v-if="hero.original_img" :src="'/images/' + hero.original_img" />
      </div>
    </div>
    <div class="hero-set">
      <div v-for="hero in legion_int" :key="hero.hero_name" class="hero">
        <img v-if="!hero.original_img" :src="'/images/' + hero.hero_img" />
        <img og v-if="hero.original_img" :src="'/images/' + hero.original_img" />
      </div>
    </div>
    <div class="hero-set">
      <div v-for="hero in hellbourne_int" :key="hero.hero_name" class="hero">
        <img v-if="!hero.original_img" :src="'/images/' + hero.hero_img" />
        <img og v-if="hero.original_img" :src="'/images/' + hero.original_img" />
      </div>
    </div>
    <div class="hero-set">
      <div v-for="hero in legion_str" :key="hero.hero_name" class="hero">
        <img v-if="!hero.original_img" :src="'/images/' + hero.hero_img" />
        <img og v-if="hero.original_img" :src="'/images/' + hero.original_img" />
      </div>
    </div>
    <div class="hero-set">
      <div v-for="hero in hellbourne_str" :key="hero.hero_name" class="hero">
        <img v-if="!hero.original_img" :src="'/images/' + hero.hero_img" />
        <img og v-if="hero.original_img" :src="'/images/' + hero.original_img" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    this.loadHeroes();
  },

  methods: {
    async loadHeroes() {
      await fetch(
        "https://ashypls.com/endpoints/apis/HN13ca016b786e40a3b49c8be8b6e57336.aspx"
      ).then((res) =>
        res.json().then((data) => {
          this.legion_agi = data.legion_agi;
          this.legion_int = data.legion_int;
          this.legion_str = data.legion_str;
          this.hellbourne_agi = data.hellbourne_agi;
          this.hellbourne_int = data.hellbourne_int;
          this.hellbourne_str = data.hellbourne_str;
        })
      );
    },
  },

  data() {
    return {
      legion_agi: [],
      legion_int: [],
      legion_str: [],
      hellbourne_agi: [],
      hellbourne_int: [],
      hellbourne_str: [],
    };
  },
};
</script>

<style lang="scss">
body{
  background:#151515;
  margin:0;
  font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
.set-wrap{
  display:grid;
  grid-template-columns: 1fr 1fr;
  gap:4rem;
  width:min-content;
  margin:auto;
  margin-top:2rem;

  .hero-set{
    display:grid;
    grid-template-columns: repeat(9,1fr);
    width:min-content;
    gap:.3rem;
  

    .hero{
      img{
        height:65px;
        width:65px;
        object-fit:cover;
        opacity:.3;

        &[og]{
          opacity:1;
          border:solid 1px gold;


        }
      }
    }
  }

}
</style>