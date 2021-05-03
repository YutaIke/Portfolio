<template>
  <div class="home">
    <transition name="slide" appear>
      <div id="nav_sns" v-show="show">
        <ul>
          <li>
            <a href="https://twitter.com/YutaIke3" target="_blank"><i class="fab fa-twitter fa-lg"></i></a>
          </li>
          <li>
            <a href="https://www.instagram.com/ike.yt_0922/?hl=ja" target="_blank"><i class="fab fa-instagram fa-lg"></i></a>
          </li>
          <li>
            <a href="https://www.facebook.com/yuta.ike.77/" target="_blank"><i class="fab fa-facebook-f fa-lg"></i></a>
          </li>
          <li>
            <a href="https://github.com/YutaIke" target="_blank"><i class="fab fa-github fa-lg"></i></a>
          </li>
          <!-- <li>
            <a href="https://qiita.com/yutaIke" target="_blank">
              <i class="fa fa-square fa-stack-2x fa-lg"></i>
              <i class="fa fa-search fa-stack-1x fa-inverse fa-sm"></i>
            </a>
          </li> -->
        </ul>
      </div>
    </transition>
    <Splash />
    <Profile />
    <Skill />
    <Works />
    <Contact />
  </div>
</template>

<script>
// @ is an alias to /src
import Splash from '@/components/Splash.vue'
import Profile from '@/components/Profile.vue'
import Skill from '@/components/Skill.vue'
import Works from '@/components/Works.vue'
import Contact from '@/components/Contact.vue'

export default {
  name: 'Home',
  components: {
    Splash,
    Profile,
    Skill,
    Works,
    Contact
  },
  data () {
    return {
      show: true
    }
  }
}
</script>

<style scoped>
#nav_sns {
  width: 25px;
  padding: 7px 5px 2px 5px;
  position: fixed;
  right: 30px;
  bottom: 30px;
  z-index: 9999;
  background-color: #fff;
  border-radius: 7px;
}

#nav_sns li {
  margin-top: 10px;
}

#nav_sns a {
  display: block;
  width: 25px;
  height: 25px;
  color: #000;
}

#nav_sns a:hover {
  -webkit-transform: scale(1.2,1.2);
  -moz-transform: scale(1.2,1.2);
  -o-transform: scale(1.2,1.2);
  -ms-transform: scale(1.2,1.2);
  transform: scale(1.2,1.2);
  transition: transform 0.1s;
  opacity: 0.5;
}

.slide-enter-active, .slide-leave-active {
  transition: transform 2s;
}

.slide-enter, .slide-leave-to {
  -webkit-transform: translate3d(0, -200vh, 0);
  transform: translate3d(0, -200vh, 0);
}

.slide-enter-to, .slide-leave {
  -webkit-transform: translate3d(0, 0, 0);
  transform: translate3d(0, 0, 0);
}

@media screen and (max-width: 767px) {
  #nav_sns {
    width: 25px;
    padding: 7px 5px 2px 5px;
    position: fixed;
    right: 15px;
    bottom: 25px;
    z-index: 9999;
    background-color: #fff;
    border-radius: 7px;
  }
}
</style>
