<template>
  <div class="header-wrap">
    <header id="header">
      <div class="navbar" v-bind:class="{light: isScreentTop}">
        <nav>
          <div class="container">
            <ul class="clearfix">
              <li><a href="#profile" v-smooth-scroll="{ duration: 2000, offset: -123 }">Profile</a></li>
              <li><a href="#skill" v-smooth-scroll="{ duration: 2000 }">Skill Set</a></li>
              <li><a href="#works" v-smooth-scroll="{ duration: 2000 }">Works</a></li>
              <li><a href="#contact" v-smooth-scroll="{ duration: 2000 }">Contact</a></li>
              <!-- <li><a href="#blog" v-smooth-scroll="{ duration: 2000 }">Blog</a></li> -->
            </ul>
          </div>
        </nav>
      </div>
      <div class="header-sp">
        <div class="header-menu">
          <div class="header-menu-line" @click="naviOpen" :class="{'is-active': active}">
            <span></span>
            <span></span>
            <span></span>
          </div>
        </div>
      </div>
    </header>
    <transition name="navi">
      <nav class="navi" v-show="navi">
        <ul class="navi-wrap">
          <li><a href="#">Profile</a></li>
          <li><a href="#">Works</a></li>
          <li><a href="#">Skill</a></li>
          <li><a href="#">Contact</a></li>
          <li><a href="#">Blog</a></li>
        </ul>
      </nav>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      active: false,
      navi: false,
      scrollY: 0
    }
  },
  mounted () {
    window.addEventListener('scroll', this.onScroll)
  },
  computed: {
    isScreentTop () {
      if (this.scrollY > 0) {
        return true
      } else {
        return false
      }
    }
  },
  methods: {
    onScroll () {
      this.scrollY = window.pageYOffset
    },
    naviOpen: function () {
      this.active = !this.active
      this.navi = !this.navi
    }
  }
}
</script>

<style scoped>
#header {
  position: fixed;
  width: 100%;
  /* background-color: rgba(8, 33, 31, 0.8); */
  /* height: 60px; */
  z-index: 100000;
}

.navbar {
  display: block;
  overflow: hidden;
  height: 60px;
  padding: 15px 0;
  transition: padding 0.5s ease, background 0.5s ease, box-shadow 0.5s ease, border 0.5s ease;
}

.navbar nav {
  width: 100%;
  /* height: 60px; */
}

.navbar .container {
  width: 80%;
  height: 100%;
  margin: 0 auto;
}

.navbar ul {
  list-style: none;
  float: right;
}

.navbar li {
  width: 100px;
  text-align: center;
  float: left;
  height: 60px;
  line-height: 60px;
}

.navbar a {
  display: block;
  color: #fff;
  width: 100%;
}

.navbar ul li a:hover {
  background-color: rgba(255,255,255,0.2);
  /* color: #fff; */
  transition: background-color .3s;
}

.light {
  padding: 0;
  background-color: #fff;
  border-bottom: solid 1px #dddddd;
  box-shadow: 0px 2px 3px rgb(0 0 0 / 4%);
  transition: padding 0.5s ease, background 0.5s ease, box-shadow 0.5s ease, border 0.5s ease;
}

.light ul li a {
  color: rgba(8, 33, 31, 0.8);
}

.light ul li a:hover {
  /* background-color: teal; */
  background-color: rgb(60, 146, 146);
  color: #fff;
  transition: background-color .3s;
}

.header-sp{
  display: none;
}

/**
* スマートフォン / タブレット
*/
@media screen and (max-width:767px) {
  /* .navbar {
    display: none;
  }

  .header-sp{
    display: block;
  } */

  .navbar {
    display: block;
    overflow: hidden;
    height: 45px;
    padding: 10px 0;
    transition: padding 0.5s ease, background 0.5s ease, box-shadow 0.5s ease, border 0.5s ease;
  }

  .navbar nav {
    width: 100%;
    /* height: 60px; */
  }

  .navbar .container {
    width: 100%;
    height: 100%;
    margin: 0 auto;
  }

  .navbar ul {
    float: none;
    width: 310px;
    margin: 0 auto;
  }

  .navbar li {
    width: 75px;
    text-align: center;
    float: left;
    height: 45px;
    line-height: 45px;
  }

  .light {
    padding: 0;
    background-color: #fff;
    border-bottom: solid 1px #dddddd;
    box-shadow: 0px 2px 3px rgb(0 0 0 / 4%);
    transition: padding 0.5s ease, background 0.5s ease, box-shadow 0.5s ease, border 0.5s ease;
  }

  /* .header-menu {
    width: 60px;
    height: 60px;
    position: fixed;
    top: 0;
    right: 0;
    z-index: 999;
  }

  .header-menu-line {
    width: 36px;
    height: 30px;
    margin-top: 15px;
    margin-left: auto;
    margin-right: auto;
    position: relative;
    cursor: pointer;
  }

  .header-menu-line span {
    width: 100%;
    height: 2px;
    background: #fff;
    display: block;
    transition: .6s;
    position: absolute;
  }

  .header-menu-line span:first-child {
    top: 0;
  }
  .header-menu-line span:nth-child(2) {
    top: 14px;
  }
  .header-menu-line span:last-child {
    bottom: 0;
  }

  .header-menu .is-active span {
    transition: .6s;
  }
  .header-menu .is-active span:first-child {
    transform: rotate(45deg);
    top: 50%;
  }
  .header-menu .is-active span:nth-child(2) {
    opacity: 0;
  }
  .header-menu .is-active span:last-child {
    transform: rotate(-45deg);
    top: 50%;
  }

  .navi {
    width: 100%;
    height: 100vh;
    display: flex;
    position: fixed;
    justify-content: center;
    align-items: center;
    color: #fff;
    background-color: #fff;
    z-index: 100;
    top: 0;
  }

  .navi-wrap {
    list-style-type: none;
    text-align: center;
    padding-left: 0;
    background: #4b4b4b;
    padding: 60px 0;
    width: 250px;
  }
  .navi-wrap li a {
    text-decoration: none;
    color: #fff;
    display: block;
    padding: 10px 100px;
  }
  .navi-enter, .navi-leave-to {
      opacity: 0;
  }
  .navi-enter-to, .navi-leave {
    opacity: 1;
  }
  .navi-enter-active, .navi-leave-active {
    transition: .6s;
  } */
}
</style>
