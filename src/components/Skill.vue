<template>
  <div id="skill" class="bg-blar" :class="{safari: safari}" v-parallax="{
        height: '100vh',
        denominator: 1.8
    }">
    <FadeInComponent>
      <h1 class="title">Skill Set</h1>
    </FadeInComponent>
    <SlideInLefttoRightComponent>
      <section>
        <div class="clearfix">
          <h2>言語・フレームワーク</h2>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>Swift / Objective-C</span>
              <el-progress :percentage="80"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>Kotlin / Java</span>
              <el-progress :percentage="70"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>HTML / CSS</span>
              <el-progress :percentage="60"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>JavaScript</span>
              <el-progress :percentage="50"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>PHP</span>
              <el-progress :percentage="50"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>C/C++</span>
              <el-progress :percentage="50"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>MySQL</span>
              <el-progress :percentage="50"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>Vue.js</span>
              <el-progress :percentage="40"></el-progress>
            </div>
          </div>
        </div>
      </section>
    </SlideInLefttoRightComponent>

    <SlideInRighttoLeftComponent>
      <section>
        <div class="clearfix">
          <h2>開発スキル</h2>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>スクラム開発</span>
              <el-progress :percentage="80"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>AWS</span>
              <el-progress :percentage="70"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>Linux</span>
              <el-progress :percentage="50"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>Git</span>
              <el-progress :percentage="70"></el-progress>
            </div>
          </div>
        </div>
      </section>
    </SlideInRighttoLeftComponent>

    <SlideInLefttoRightComponent>
      <section>
        <div class="clearfix">
          <h2>その他</h2>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>Jira / Confluence</span>
              <el-progress :percentage="80"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>GitHub</span>
              <el-progress :percentage="80"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>jenkins</span>
              <el-progress :percentage="50"></el-progress>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>安全確保支援士</span>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>認定スクラムマスター</span>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>認定プロダクトオーナー</span>
            </div>
          </div>
          <div class="progress-col">
            <div class="progress-wrapper">
              <span>AWS認定ソリューションアーキテクト アソシエイト</span>
            </div>
          </div>
        </div>
      </section>
    </SlideInLefttoRightComponent>

  </div>
</template>

<script>
// import SkillChart from '@/components/SkillChart.vue'
import FadeInComponent from '@/components/FadeInComponent.vue'
import SlideInLefttoRightComponent from '@/components/SlideInLefttoRightComponent.vue'
import SlideInRighttoLeftComponent from '@/components/SlideInRighttoLeftComponent.vue'

export default {
  name: 'Skill',
  components: {
    // SkillChart,
    FadeInComponent,
    SlideInLefttoRightComponent,
    SlideInRighttoLeftComponent
  },
  data () {
    return {
      safari: false
    }
  },
  directives: {
    parallax: {
      inserted (el, binding) {
        el.setAttribute( // 初期状態のスタイル
          'style',
            `
              background-position: center top;
              background-size: initial;
              backgroung-repeat: no-repeat;
              background-position-y: ${window.scrollY / binding.value.denominator}px;
            `
        )
        window.addEventListener('scroll', () => {
          el.setAttribute( // スクロール量に応じて動的に変化するスタイル
            'style',
            `
              background-position: center center;
              background-size: initial;
              backgroung-repeat: no-repeat;
              background-position-y: ${window.scrollY / binding.value.denominator + 300}px;
            `
          )
        })
      }
    }
  },
  created: function () {
    var userAgent = window.navigator.userAgent.toLowerCase()
    if (userAgent.indexOf('safari') !== -1 && userAgent.indexOf('chrome') === -1 && userAgent.indexOf('edge') === -1) {
      this.safari = true
    } else {
      this.safari = false
    }
  }
}
</script>

<style scoped>
#skill {
  padding: 100px 10%;
  width: 100%;
  margin: 0 auto;
  box-sizing: border-box;
  position: relative;
  background-image: url('../assets/background-contact.jpg');
  z-index: 0;
}

.safari {
  background-position-y: center !important;
}

section {
  margin-bottom: 25px;
}

section h2 {
  text-align: left;
  color: white;
}

.bg-blar:before{
  content: '';
  background: inherit;
  -webkit-filter: blur(5px) brightness(0.8);
  -moz-filter: blur(5px) brightness(0.8);
  -o-filter: blur(5px) brightness(0.8);
  -ms-filter: blur(5px) brightness(0.8);
  filter: blur(5px) brightness(0.8);
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  z-index: -1;
}

.title{
  text-align: left;
  margin-bottom: 40px;
  color: rgb(60, 146, 146);
  font-weight: 600;
  letter-spacing: 0.2em;
}

.container {
  position: relative;
}

.skill-chart {
  float: left;
  width: 30%;
  padding: 10px;
  background-color: #fff;
  border: solid 1px #ddd;
  box-shadow: 0px 2px 3px rgb(0 0 0 / 4%);
  box-sizing: border-box;
}

.skill-chart:nth-child(1),
.skill-chart:nth-child(2) {
  margin-right: 4%;
}

.progress-col {
  width: 33.3333333333%;
  margin-left: auto;
  left: auto;
  right: auto;
  float: left;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
  padding: 0.75rem;
}

.progress-wrapper {
  padding: 10px 5px;
  background-color: rgba(255, 255, 255, 1);
  border: 0;
  border-radius: 0.1875rem;
  box-shadow: 0px 5px 25px 0px rgb(0 0 0 / 20%);
}

@media screen and (max-width: 767px) {
  #skill {
    padding: 20px 10px;
    width: 100%;
    margin: 0 auto;
    box-sizing: border-box;
    position: relative;
    background-image: url('../assets/background-contact.jpg');
    z-index: 0;
  }

  .title {
    text-align: center;
  }

  section h2 {
    text-align: center;
  }

  .progress-col {
    width: 100%;
    float: none;
    padding: 15px 10px;
  }
}
</style>
