<template>
  <div id="app" >
    <hero id="hero" :scroll-pos="this.scroll"></hero>
    <features/>
    <testimonials/>
    <div class="footer">
      <div class="container">
        <div class="row" style="margin-bottom:0;">
          <div class="col s12">
            <ul style="text-align:center">
              <li><a href="www.facebook.com"><i class="fa fa-facebook"></i></a></li>
              <li><a href="www.google.com"><i class="fa fa-google"></i></a></li>
              <li><a href="www.twitter.com"><i class="fa fa-twitter"></i></a></li>
              <li><a href="www.linkedin.com"><i class="fa fa-linkedin"></i></a></li>
            </ul>
          </div>
         <div class="col s12 footer-links" style="text-align:center">
           © Deskera 2017-2020 | <a href="#hero">Terms of Service</a> | <a href="#hero">Privacy Policy</a> |  <a href="#hero">About Us</a> |  <a href="#hero">Contact Us</a> | ISO 9001 Certified 
         </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Hero from './components/Hero.vue';
import Features from './components/Features.vue'
import Testimonials from './components/Testimonials.vue'
export default {
  name: 'app',
  data() {
    return {
      scroll:0
    }
  },
  components: {
    Hero,
    Features,
    Testimonials
  },methods: {
    initScroll:function(e) {
     var bodyScrollTop = document.documentElement.scrollTop || document.body.scrollTop;
      this.scroll = bodyScrollTop;
    }
  }, created () {
    window.addEventListener('scroll', this.initScroll);
  },
  destroyed () {
    window.removeEventListener('scroll', this.initScroll);
  }

}
</script>

<style>
body {
  padding:0;
  margin:0;
  font-family: 'Roboto', sans-serif;
}
.footer {
  background-color: #d40d12;
  color: #fff;
  height: auto;
}
.footer ul {
  margin: 0;
  padding:10px;
  box-sizing: border-box;
  color:#fff
}

.footer ul li{
  margin-right: 25px;
  display: inline-block;
}


.footer ul li a{
  color:#FFF;
  font-size: 14px;
}
.footer-links a {
  color:#fff;
  text-decoration: underline;
}
</style>
