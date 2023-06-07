<template>
  <div class="key">
    <div class="key-item">
      <div class="box" bd></div>
      <div class="box-desc">= Bad at Midwars</div>
    </div>

    <div class="key-item">
      <div class="box" gd></div>
      <div class="box-desc">= Good at Midwars</div>
    </div>

    <div class="key-item">
      <div class="box" ham>
        <i class="bx bxs-no-entry"></i>
      </div>
      <div class="box-desc">= Ban Worthy Hero</div>
    </div>
  </div>
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
        <div :goodmw="hero.midwars_good" tt class="tt">
          <img pp :src="'/images/' + hero.hero_img" />
          <span>{{ nameHotFix(hero.hero_name) }}</span>
        </div>
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
        <div :goodmw="hero.midwars_good" tt class="tt">
          <img pp :src="'/images/' + hero.hero_img" />
          <span>{{ nameHotFix(hero.hero_name) }}</span>
        </div>
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
        <div :goodmw="hero.midwars_good" tt class="tt">
          <img pp :src="'/images/' + hero.hero_img" />
          <span>{{ nameHotFix(hero.hero_name) }}</span>
        </div>
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
        <div :goodmw="hero.midwars_good" tt class="tt">
          <img pp :src="'/images/' + hero.hero_img" />
          <span>{{ nameHotFix(hero.hero_name) }}</span>
        </div>
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
        <div :goodmw="hero.midwars_good" tt class="tt">
          <img pp :src="'/images/' + hero.hero_img" />
          <span>{{ nameHotFix(hero.hero_name) }}</span>
        </div>
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
        <div :goodmw="hero.midwars_good" tt class="tt">
          <img pp :src="'/images/' + hero.hero_img" />
          <span>{{ nameHotFix(hero.hero_name) }}</span>
        </div>
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
    nameHotFix(name) {
      if (name == "Arachna") {return "Dirty Stinky Spidery Bitch";};
      if (name == "Artillery") {return "No.";};
      if (name == "Empath") {return "Ash's Buttplug";};
      //new ones below
      if (name == "Thunderbringer") {return "Show you my HS.. Clown?";};
      if (name == "Artillery") {return "No.";};
      if (name == "Artillery") {return "No.";};
      if (name == "Artillery") {return "No.";};
      return name;
    },
    showPP(element) {
      element.querySelector("[og]")?.setAttribute("show", "");
      element.querySelector("[tt]")?.setAttribute("show", "");
    },
    hidePP(element) {
      element.querySelector("[og]")?.removeAttribute("show");
      element.querySelector("[tt]")?.removeAttribute("show");
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
.key {
  background: rgb(12, 12, 12);
  padding: 2rem;
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

      .tt {
        position: absolute;
        background: rgb(30, 30, 30);
        top: 0;
        left: 100px;
        z-index: 99999;
        padding: 1rem;
        border-radius: 0.5rem;
        color: white;
        opacity: 0;
        pointer-events: none;
        user-select: none;
        white-space: nowrap;
        display: flex;
        flex-direction: column;
        gap: 0.5rem;
        align-items: center;
        justify-content: center;
        outline: solid 5px rgb(156, 13, 13);

        -webkit-box-shadow: 0px 0px 46px 12px rgba(0, 0, 0, 0.75);
        -moz-box-shadow: 0px 0px 46px 12px rgba(0, 0, 0, 0.75);
        box-shadow: 0px 0px 46px 12px rgba(0, 0, 0, 0.75);

        span {
          pointer-events: none;
          user-select: none;
        }

        &[goodmw="1"] {
          outline: solid 5px rgb(40, 158, 50);

          img {
            outline: solid 5px rgb(40, 158, 50);
            pointer-events: none;
            user-select: none;
          }
        }

        img {
          border-radius: 50%;
          opacity: 1 !important;
        }

        transition: all 200ms ease;
        &[show] {
          opacity: 1;
        }
      }

      i {
        z-index: 999;
        position: absolute;
        color: red;
        font-size: 150%;
        top: 0.25rem;
        right: 0.25rem;
        opacity: 0.8;
      }

      &[goodmw="1"] {
        border: solid 3px rgb(71, 121, 51);
        img {
          opacity: 0.1;
        }
      }
      &[goodmw="0"] {
        border: solid 3px rgb(75, 35, 35);
        img {
          opacity: 0.1;
        }
      }

      img {
        height: 65px;
        width: 65px;
        object-fit: cover;
        cursor: pointer;

        &[og] {
          opacity: 1;
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
      }
    }
  }
}
.key {
  color: white;
  display: flex;
  flex-direction: row;
  gap: 1rem;
  justify-content: center;
  align-items: center;

  .key-item {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    gap: 1rem;

    .box {
      height: 65px;
      width: 65px;
      position: relative;

      &[gd] {
        border: solid 3px rgb(71, 121, 51);
      }

      &[bd] {
        border: solid 3px rgb(75, 35, 35);
      }

      &[ham] {
        border: solid 3px rgb(59, 59, 59);
        i {
          position: absolute;
          top: 0.25rem;
          right: 0.25rem;
          color: red;
          font-size: 150%;
        }
      }
    }
  }
}
</style>