<template>
  <div class="set-wrap">
    <div class="hero-set">
      <div
        @mouseenter="showPP($event.target)"
        @mouseleave="hidePP($event.target)"
        v-for="hero in legion_agi"
        :goodmw="hero.midwars_good"
        :key="hero.hero_name"
        class="hero"
      >
        <i v-show="hero.ban_worthy == 1" class="bx bxs-no-entry"></i>
        <img pp :src="'/images/' + hero.hero_img" />
        <img
          og
          v-if="hero.original_img"
          :src="'/images/' + hero.original_img"
        />
      </div>
    </div>
    <div class="hero-set">
      <div
        @mouseenter="showPP($event.target)"
        @mouseleave="hidePP($event.target)"
        v-for="hero in hellbourne_agi"
        :key="hero.hero_name"
        :goodmw="hero.midwars_good"
        class="hero"
      >
        <i v-show="hero.ban_worthy == 1" class="bx bxs-no-entry"></i>
        <img pp :src="'/images/' + hero.hero_img" />
        <img
          og
          v-if="hero.original_img"
          :src="'/images/' + hero.original_img"
        />
      </div>
    </div>
    <div class="hero-set">
      <div
        @mouseenter="showPP($event.target)"
        @mouseleave="hidePP($event.target)"
        v-for="hero in legion_int"
        :goodmw="hero.midwars_good"
        :key="hero.hero_name"
        class="hero"
      >
        <i v-show="hero.ban_worthy == 1" class="bx bxs-no-entry"></i>
        <img pp :src="'/images/' + hero.hero_img" />
        <img
          og
          v-if="hero.original_img"
          :src="'/images/' + hero.original_img"
        />
      </div>
    </div>
    <div class="hero-set">
      <div
        @mouseenter="showPP($event.target)"
        @mouseleave="hidePP($event.target)"
        v-for="hero in hellbourne_int"
        :goodmw="hero.midwars_good"
        :key="hero.hero_name"
        class="hero"
      >
        <i v-show="hero.ban_worthy == 1" class="bx bxs-no-entry"></i>
        <img pp :src="'/images/' + hero.hero_img" />
        <img
          og
          v-if="hero.original_img"
          :src="'/images/' + hero.original_img"
        />
      </div>
    </div>
    <div class="hero-set">
      <div
        @mouseenter="showPP($event.target)"
        @mouseleave="hidePP($event.target)"
        v-for="hero in legion_str"
        :goodmw="hero.midwars_good"
        :key="hero.hero_name"
        class="hero"
      >
        <i v-show="hero.ban_worthy == 1" class="bx bxs-no-entry"></i>
        <img pp :src="'/images/' + hero.hero_img" />
        <img
          og
          v-if="hero.original_img"
          :src="'/images/' + hero.original_img"
        />
      </div>
    </div>
    <div class="hero-set">
      <div
        @mouseenter="showPP($event.target)"
        @mouseleave="hidePP($event.target)"
        v-for="hero in hellbourne_str"
        :goodmw="hero.midwars_good"
        :key="hero.hero_name"
        class="hero"
      >
        <i v-show="hero.ban_worthy == 1" class="bx bxs-no-entry"></i>
        <img pp :src="'/images/' + hero.hero_img" />
        <img
          og
          v-if="hero.original_img"
          :src="'/images/' + hero.original_img"
        />
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
      await fetch("hon-heroes.json").then((res) =>
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
    showPP(element) {
      element.querySelector("[og]")?.setAttribute("show", "");
    },
    hidePP(element) {
      element.querySelector("[og]")?.removeAttribute("show");
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
body {
  background: #151515;
  margin: 0;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
.set-wrap {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  width: min-content;
  margin: auto;
  margin-top: 2rem;

  .hero-set {
    display: grid;
    grid-template-columns: repeat(9, 1fr);
    width: min-content;
    gap: 0.3rem;

    .hero {
      position: relative;
      height: 65px;
      width: 65px;


      i {
        z-index: 9999999;
        position: absolute;
        color: red;
        font-size: 150%;
        top: 0.25rem;
        right: 0.25rem;
        opacity: 0.8;
      }

      &[goodmw="1"] {
        border: solid 2px rgb(59, 91, 46);
        img {
          opacity: 0.3;
        }
      }
      &[goodmw="0"] {
        border: solid 2px rgb(75, 35, 35);
        img {
          opacity: 0.05;
        }
      }

      img {
        height: 65px;
        width: 65px;
        object-fit: cover;
        cursor: pointer;

        &[og] {
          opacity: 1;
          border: solid 1px gold;
          position: absolute;
          top: 0;
          left: 0;
          z-index: 9999;
          transform: none;
          transition: transform 200ms ease;

          &[show] {
            transform: translateX(85%) rotate(25deg) translateY(-25%);
          }
        }

        &[pp] {
        }
      }
    }
  }
}
</style>