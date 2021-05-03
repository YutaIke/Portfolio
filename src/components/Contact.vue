<template>
  <div id="contact" class="bg-blar" v-parallax="{
        height: '100vh',
        denominator: 1.8
    }">
    <h1 class="title">Contact</h1>
    <p>閲覧ありがとうございました。もしコメント等ありましたらお気軽にご連絡いただけますと幸いです。</p>
    <a href="mailto:kei.yt22.biz@gmail.com">kei.yt22.biz@gmail.com</a>
  </div>
</template>

<script>
export default {
  name: 'Contact',
  data () {
    return {
      name: '',
      email: '',
      content: ''
    }
  },
  directives: {
    parallax: {
      inserted (el, binding) {
        el.setAttribute( // 初期状態のスタイル
          'style',
            `
              background-position: center top;
              background-size: cover;
              backgroung-repeat: no-repeat;
              background-position-y: ${window.scrollY / binding.value.denominator}px;
            `
        )
        window.addEventListener('scroll', () => {
          el.setAttribute( // スクロール量に応じて動的に変化するスタイル
            'style',
            `
              background-position: center center;
              background-size: cover;
              backgroung-repeat: no-repeat;
              background-position-y: ${window.scrollY / binding.value.denominator + 200}px;
            `
          )
        })
      }
    }
  }
}
</script>

<style scoped>
#contact {
  background-color: #F3F3F3;
  width: 100%;
  padding: 100px 150px;
  box-sizing: border-box;
  position: relative;
  z-index: 0;
  line-height: 1.6;
}

a:hover {
  opacity: 0.7;
}

.bg-blar:before{
  content: '';
  background: inherit;
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  z-index: -1;
}

.title {
  text-align: left;
  margin-bottom: 40px;
  color: rgb(60, 146, 146);
  font-weight: 600;
  letter-spacing: 0.2em;
}

.form {
  width: 75%;
  margin: 0 auto;
}

button.submit {
  width: 100%;
}

@media screen and (max-width: 767px) {
  #contact {
    padding: 20px 10px;
    box-sizing: border-box;
    line-height: 1.6;
  }

  .title{
    text-align: center;
    margin-bottom: 0px;
  }
}
</style>
