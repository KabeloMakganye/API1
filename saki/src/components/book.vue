<template @resize="removemenu">
<div >
<div class="container">

  <div class="book">
    <div class="gap"></div>
    <div class="pages">
      <div class="page"></div>
      <div class="page"></div>
      <div class="page"></div>
      <div class="page"></div>
      <div class="page"></div>
      <div class="page"></div>
    </div>
    <div class="flips">
      <div class="flip flip1">
        <div class="flip flip2">
          <div class="flip flip3">
            <div class="flip flip4">
              <div class="flip flip5">
                <div class="flip flip6">
                  <div class="flip flip7"></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

</div>
</template>

<script>
import axios from 'axios'
import swal from 'sweetalert'
export default {
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      file: '1111',
      sugname: '',
      sugemail: '',
      sugmessage: '',
      resultsFetched_3: '',

      // Sign ub variables
      signname: '',
      signsurname: '',
      signcarname: '',
      signcarreg: '',
      signemail: '',
      signupPass: '',
      signupPassCon: '',
      signnumber: '',
      pic: null
    }
  },
  mounted () {
    window.addEventListener('resize', this.removemenu)
  },
  /* unmounted () {
    window.removeEventListener('resize', this.removemenu)
  }, */
  methods: {
    addprice () {
      document.querySelector('nav').classList.add('menu-btn')
      document.getElementById('blur2').style.width = '100%'
    },
    addmenu () {
      document.querySelector('nav').classList.add('menu-btn')
      document.getElementById('blur').style.width = '100%'
    },
    removemenu () {
      document.getElementById('blur').style.width = '0%'
      document.querySelector('nav').classList.remove('menu-btn')
    },
    upload (event) {
      // await fetch(`https://kabelodatabase.herokuapp.com/set_pic/${this.$refs.myFiles.files}`)
      this.pic = event.target.files[0]
    },
    async uploadpic () {
      const fd = new FormData()
      console.log(this.pic)
      fd.append('image', this.pic, this.pic.name)
      axios.post(`https://kabelodatabase.herokuapp.com/image`, {
        todo: this.pic
      })
        .then(res => {
          console.log(res)
        })
    },
    async register () {
      if (this.signupPass === this.signupPassCon) {
        document.getElementById('sendesugg').disabled = true
        document.getElementById('sendesugg').style.backgroundColor = '#F0998B'
        let allAreFilled = true /* check if all required fields are entered */
        document.getElementById('suggestions').querySelectorAll('[required]').forEach(function (i) {
          if (!allAreFilled) return
          if (!i.value) allAreFilled = false
        })
        if (allAreFilled) {
          const axios = require('axios')
          await axios.post('https://kabelodatabase.herokuapp.com/register', {
            name: this.signname,
            surname: this.signsurname,
            carname: this.signcarname,
            carreg: this.signcarreg,
            email: this.signemail,
            password: this.signupPass,
            celnum: this.signnumber
          })
            .then((response) => {
              console.log(response)
              // alert(response.data)
              if (response.data === 'Invalid email') {
                swal('Invalid email', '', 'error')
              } else if (response.data === 'Something went wrong. please try again.') {
                swal('Something went wrong', '', 'error')
              } else if (response.data === 'user already registered') {
                swal('User already registered', '', 'error')
              } else {
                swal('User registered, copy of login details sent to your email', '', 'success')
                this.signname = ''
                this.signsurname = ''
                this.signcarname = ''
                this.signcarreg = ''
                this.signemail = ''
                this.signupPass = ''
                this.signnumber = ''
                this.signupPassCon = ''
              }
            }, (error) => {
              console.log(error)
            })
        } else {
          // alert('fill up everything')
          swal('fill up everything', '', 'error')
        }
      } else {
        // alert('Passwords are not the same')
        swal('Passwords are not the same', '', 'error')
      }
      document.getElementById('sendesugg').disabled = false
      document.getElementById('sendesugg').style.backgroundColor = '#31F300'
    },
    async sendemail () {
      document.getElementById('sendesugg').disabled = true
      document.getElementById('sendesugg').style.backgroundColor = '#F0998B'
      let allAreFilled = true /* check if all required fields are entered */
      document.getElementById('suggestions').querySelectorAll('[required]').forEach(function (i) {
        if (!allAreFilled) return
        if (!i.value) allAreFilled = false
      })
      if (allAreFilled) {
        const axios = require('axios')
        await axios.post('https://kabelodatabase.herokuapp.com/sendemail', {
          sugestionname: this.sugname,
          sugestionmessage: this.sugmessage,
          sendereamil: 'joesdrivethrough@gmail.com',
          password: this.signupPass
        })
          .then((response) => {
            this.sugname = ''
            this.sugmessage = ''
            console.log(response)
            alert(response.data)
          }, (error) => {
            console.log(error)
          })
      } else {
        alert('Enter all required fields')
      }
      document.getElementById('sendesugg').disabled = false
      document.getElementById('sendesugg').style.backgroundColor = '#31F300'
      /* await fetch(`https://kabelodatabase.herokuapp.com/sendemail/joesdrivethrough@gmail.com/` + this.sugname + ' ' + this.sugmessage)
          .then(response => response.json())
          .then(results => (this.resultsFetched_3 = results))
        alert(this.resultsFetched_3)
      } */
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
/* THE BOOK EFFECT */

@import url('https://fonts.googleapis.com/css2?family=Indie+Flower&display=swap');
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap");
@import url('https://fonts.googleapis.com/css2?family=Josefin+Slab:ital,wght@1,500&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Preahvihear&display=swap');

:root {
  --primary-color: rgb(0, 0, 0);
}
 .left-col blockquote {
  font-size: 1.2em;
  font-weight: bold;
  /* color: #31F300; */
}
.abc {
  position: relative;
  animation-name: example;
  animation-duration: 4s;
  animation-iteration-count: infinite;
  color: white;
}
@keyframes example {
  0%   { left:-15px; top:0px;}
  50%  { left:15px; top:0px;}
  100%  {left:-15px; top:0px;}
}
.aboutimg2 {
  background-color: rgb(255,227,24,0.9);
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  margin-bottom: 25px;
  padding-left: 10px;
  padding-top: 10px;
  padding-right: 10px;
  padding-bottom: 10px;
  border-radius: 25px;
}
.aboutimg3 {
  color: white;
  background-color: rgb(255,227,24,0.9);
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  margin-bottom: 25px;
}
.aboutimg {
    /* background-color: white; */
  box-shadow: 0 4px 8px 0 rgba(255, 242, 0, 0.2), 0 6px 20px 0 rgba(255, 242, 0, 0.19);
 margin-bottom: 25px;
}
.left-col cite {
   font-size: 1.0em;
}
p {
  font-family: 'Josefin Slab', serif;
  color: black;
}

body {
  background: rgba(0, 0, 0, 100);
  margin: 0;
  font-family: 'Poppins';
}

.navbar {
  background: black;
  padding: 1em;
}

.navbar .logo {
  text-decoration: none;
  font-weight: bold;
  color: black;
  font-size: 1.2em;
}

.navbar .logo span {
  color: var(--primary-color);
}

.navbar nav {
  display: none;
  transition: 0.5s;
}

.navbar .container {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  place-content: space-between;
}

.navbar .mobile-menu {
  cursor: pointer;
}

a {
  color: #444444;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

section {
  padding: 5em 2em;
}

.hero {
  /* text-align: center; */
      background:url('../assets/soren-h-1PKAYeA_nZ4-unsplash.jpg');
     /* background-image-opacity: 0.2; */
      background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: center;
}
.hero12 {
  text-align: center;
      /* background:url('../assets/108487139-window-wash-1440.jpg'); */
      /* background-image-opacity: 0.2; */
}

.left-col .subhead {
  text-transform: uppercase;
  font-weight: bold;
  color: gray;
  letter-spacing: .3em;
}

.left-col h1 {
  font-size: 2.5em;
  line-height: 1.3em;
  margin-top: .2em;
  color: #000000;
}

.left-col .primary-cta {
  background: var(--primary-color);
  color: white;
  text-decoration: none;
  padding: .6em 1.3em;
  font-size: 1.4em;
  border-radius: 5em;
  font-weight: bold;
  display: inline-block;
}

.left-col .watch-video-cta {
  display: block;
  margin-top: 1em;
}

.left-col .watch-video-cta img {
  margin-right: .5em;
}

.hero-img {
  width: 70%;
  margin-top: 3em;
}

.hero-img2 {
  width: 100%;

  opacity: 0.98;

  border: 0.5px solid var(--primary-color);
  border-radius: 1%;
  /* margin-top: -4.5em; */
}

section.features-section {
  background: #20272E;
  color: white;
}

ul.features-list {
  margin: 0;
  padding-left: .1em;
  display: -ms-grid;
  display: grid;
  -ms-grid-columns: (minmax(19rem, 1fr))[auto-fit];
      grid-template-columns: repeat(auto-fit, minmax(19rem, 1fr));
}

ul.features-list li {
  font-size: 1.1em;
  margin-bottom: 1em;
  margin-left: 2em;
  position: relative;
}

ul.features-list li:before {
  content: '';
  left: -2em;
  position: absolute;
  width: 20px;
  height: 20px;
  background-image: url("../assets/bullet.svg");
  background-size: contain;
  margin-right: .5em;
}

.features-section img {
  display: none;
}

.testimonials-section {
  background: var(--primary-color);
  color: white;
  padding: 1em 1em;
}
.testimonials-section2 {
  background: rgba(109, 104, 104, 0.2);
  color: white;
  padding: 1em 1em;
}

.testimonials-section li {
    color: rgb(255,227,24);
  padding: .5em;
  font-size: 1em;
  text-align: left;
  /* background: #006BD6;
  text-align: center;
  padding: 2em 1em;
  width: 80%;
  margin: 0 auto 5em auto;
  border-radius: 1em; */
}

.testimonials-section li img {
 /* width: 5em;
  height: 5em;
  border: 5px solid #006BD6;
  border-radius: 50%;
  margin-top: -4.5em; */
}

h2 {
  font-size: 2em;
  color: rgb(255,227,24,0.9);
}

label {
  display: block;
  font-size: 1.2em;
  margin-bottom: .5em;
}

input, textarea {
  width: 100%;
  padding: .8em;
  margin-bottom: 1em;
  border-radius: .3em;
  border: 1px solid rgb(45,62,80);
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
}

input[type="button"] {
  background-color: rgb(45,62,80);
  color: white;
  font-weight: bold;
  font-size: 1.3em;
  border: none;
  margin-bottom: 0em;
  border-radius: 5em;
  display: inline-block;
  padding: .8em 2em;
  width: unset;
  cursor: pointer;
}

iframe {
  width: 100%;
  height: 300px;
}

nav.menu-btn {
  display: block;
}

nav {
  position: fixed;
  z-index: 999;
  width: 66%;
  right: 0;
  top: 0;
  background:  rgba(0, 0, 0, 0.90);
  height: 100vh;
  padding: 1em;
}

nav ul.primary-nav {
  margin-top: 5em;
}

nav li a {
  color: rgb(255,227,24);
  text-decoration: none;
  display: block;
  padding: .5em;
  font-size: 1.3em;
  text-align: left;
}

nav li a:hover {
  font-weight: bold;
}

.mobile-menu-exit {
  float: right;
  margin: .5em;
  cursor: pointer;
}
@media screen and (max-width: 768px)  {
  input, select, textarea {
    font-size: 16px;
  }
  .navbar nav li.current a {
    color: yellowgreen;
  }
}

@media only screen and (min-width: 768px) {
  .mobile-menu, .mobile-menu-exit {
    display: none;
  }
  .navbar .container {
    display: -ms-grid;
    display: grid;
    -ms-grid-columns: 180px auto;
        grid-template-columns: 180px auto;
    -webkit-box-pack: unset;
        -ms-flex-pack: unset;
            justify-content: unset;
  }
  .navbar nav {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-pack: justify;
        -ms-flex-pack: justify;
            justify-content: space-between;
    background: none;
    position: unset;
    height: auto;
    width: 100%;
    padding: 0;
  }
  .navbar nav ul {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
  .navbar nav a {
    color: rgb(255, 225, 0);
    font-size: 1em;
    padding: .1em 1em;
  }
  .navbar nav ul.primary-nav {
    margin: 0;
  }
  .navbar nav li.current a {
    font-weight: bold;
  }
  .navbar nav li.go-premium-cta a {
    color: var(--primary-color);
    border: 3px solid var(--primary-color);
    font-weight: bold;
    border-radius: 5em;
    margin-top: -.2em;
  }
  .navbar nav li.go-premium-cta a:hover {
    background: var(--primary-color);
    color: white;
  }
  .navbardown {
  display: flex;
  place-content: space-between;
}
}

@media only screen and (min-width: 1080px) {
  .container {
    width: 100%;
    margin: 0 auto;
  }
  section {
    padding: 10em 4em;
  }
  .hero .container {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-pack: justify;
        -ms-flex-pack: justify;
            justify-content: space-between;
    text-align: left;
  }
  .hero .container .left-col {
    margin: 3em 3em 0 5em;
    background: rgba(255, 255, 255, 0.05);
     backdrop-filter: blur(8px);
  }
  .hero .container .left-col h1 {
    font-size: 3em;
    width: 90%;
  }
  .hero-img {
    width: 30%;
    margin-right: 8em;
  }
  .hero-cta {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
  .primary-cta {
    margin-right: 1em;
  }
  ul.features-list {
    display: block;
    margin-left: 5em;
  }
  ul.features-list li {
    font-size: 1.4em;
  }
  ul.features-list li:before {
    width: 30px;
    height: 30px;
  }
  .features-section {
    position: relative;
  }
  .features-section img {
    display: block;
    position: absolute;
    right: 0;
    width: 350px;
    bottom: -2em;
  }
  .testimonials-section ul {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
  .testimonials-section ul li {
    margin: 0 1em;
  }
  .contact-section {
    position: relative;
  }
  .contact-section .container {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
  .contact-left {
    position: relative;
    left: 25%;
    top: 0;
    width: 45%;
    height: 100%;
  }
  .contact-right {
    position: absolute;
    right: 0;
    top: 0;
    width: 45%;
    height: 100%;
  }
  .contact-right iframe {
    height: 100%;
  }
}

@media only screen and (min-width: 1450px) {
  .features-section:before {
    content: '';
    position: absolute;
    width: 10%;
    height: 20em;
    background: var(--primary-color);
    left: 0;
    top: -4em;
  }
  .features-section:after {
    content: '';
    position: absolute;
    width: 200px;
    height: 20em;
    background: url("../assets/dots.svg") no-repeat;
    left: 4.5em;
    top: 2em;
  }
}

@media only screen and (max-width: 1450px) {
  .hero .container .left-col {
    border: 15px;
    margin: 0em 0em 0 0em;
    background: rgba(255, 255, 255, 0.05);
     backdrop-filter: blur(8px);
  }
}
  .blur {
  background: rgba(34, 33, 33, 0.5);
  backdrop-filter: blur(8px);
  height: 100%;
  width: 0%;
  position: fixed;
  top:0 ;
  left: 0;
  overflow-x: visible;
  z-index: 3;
  transition: .8s;
}
  .blur2 {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(8px);
  /* height: 75%; */
  position: fixed;
  top:25% ;
  left: 25%;
  right: 25%;
  bottom: 25%;
  overflow-x: visible;
  z-index: 3;
  transition: .8s;
}
.price {
  z-index: 3;
  position: fixed;
  left: 30%;
  top: 20%;
}

.mySlides {display: none}
img {vertical-align: middle;}

/* Slideshow container */
.slideshow-container {
  max-width: 1000px;
  position: relative;
  margin: auto;
}

/* Next & previous buttons */
.prev, .next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  padding: 16px;
  margin-top: -22px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.6s ease;
  border-radius: 0 3px 3px 0;
  user-select: none;
  background-color: #31F300;
}

/* Position the "next button" to the right */
.next {
  right: 0;
  border-radius: 3px 0 0 3px;
}

/* On hover, add a black background color with a little bit see-through */
.prev:hover, .next:hover {
  background-color: #F0998B;
}

/* Caption text */
.text2 {
  font-weight: bold;
  color: white;
  /* font-size: 15px; */
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80%;
}

/* Number text (1/3 etc) */
.numbertext {
  color: #000000;
  font-size: 12px;
  padding: 8px 12px;
  position: absolute;
  top: 0;
}

/* The dots/bullets/indicators */
.dot {
  cursor: pointer;
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

.active, .dot:hover {
  background-color: #717171;
}

/* Fading animation */
.fade {
  animation-name: fade;
  animation-duration: 5s;
  transition: 4s ease;
  width:100%;height:500px;

}

@keyframes fade {
  from {opacity: .4}
  to {opacity: 1}
}

/* On smaller screens, decrease text size */
@media only screen and (max-width: 300px) {
  .prev, .next,.text {font-size: 11px}
}
/*# sourceMappingURL=main.css.map */
p {
  color: rgb(255,227,24);
  text-decoration: none;
  display: block;
  padding: .5em;
  font-size: 1em;
  text-align: left;
font-family: 'Preahvihear', sans-serif;
}

.centered {
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0, 0.4); /* Black w/opacity/see-through */
  color: white;
  font-weight: bold;
  border: 3px solid #f1f1f1;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  width: 80%;
  padding: 20px;
  text-align: center;
}
  .ab a {
    color: white ;/* var(--primary-color); */
    border: 3px solid white;
    font-weight: bold;
    border-radius: 5em;
    margin-top: -.2em;
    text-decoration: none;
    position: absolute;
    left:50%;
     font-size: 1.3em;
  }
  .ab a:hover {
    /* background: white; */
    color:rgb(255,227,24);
  }
  .bg-text {
  background-color: rgb(0,0,0); /* Fallback color */
  background-color: rgba(0,0,0, 0.4); /* Black w/opacity/see-through */
  color: white;
  font-weight: bold;
  border: 3px solid #f1f1f1;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  width: 80%;
  padding: 20px;
  text-align: center;
}
.imgLoader {
  position: fixed;
  animation: preLoad 1s steps(1);
  width: 1px;
  height: 1px;
}
@keyframes preLoad {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
  }
  10% {
    background-image: url('https://picsum.photos/420/300?random=2');
  }
  20% {
    background-image: url('https://picsum.photos/420/300?random=3');
  }
  30% {
    background-image: url('https://picsum.photos/420/300?random=4');
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=5');
  }
  100% {
    display: none;
  }
}
.container {
  position: relative;
  width: 420px;
  border:#000000 solid 2px;
  border-radius: 4px;
  height: 420px;
}
.title {
  position: absolute;
  top: 45px;
  left: 0;
  width: 100%;
  font-size: 2em;
  font-weight: normal;
  line-height: 1;
}
.credit {
  position: absolute;
  top: 100%;
  left: 0;
  font-size: 0.9em;
  text-align: left;
}
.book {
  position: relative;
  perspective: 630px;
  perspective-origin: center 50px;
  transform: scale(1.2);
  filter: drop-shadow(0px 10px 5px rgba(0, 0, 0, 0.25));
}
.page {
  width: 210px;
  height: 300px;
  background-color: #bbb;
  position: absolute;
  top: 0px;
  right: 50%;
  transform-origin: 100% 100%;
  border: solid #555 2px;
  background-size: 420px 300px;
  background-position: center;
  transform-style: preserve-3d;
}
.page:nth-child(1) {
  transform: rotateX(60deg) rotateY(3deg);
}
.page:nth-child(2) {
  transform: rotateX(60deg) rotateY(4.5deg);
}
.page:nth-child(3) {
  transform: rotateX(60deg) rotateY(6deg);
  animation: nextPage 25s infinite -24s steps(1);
  background-size: 420px 300px;
  background-position: -2px -2px;
}
.page:nth-child(4) {
  transform: rotateX(60deg) rotateY(177deg);
}
.page:nth-child(5) {
  transform: rotateX(60deg) rotateY(175.5deg);
}
.page:nth-child(6) {
  transform: rotateX(60deg) rotateY(174deg);
  overflow: hidden;
}
.page:nth-child(6)::after {
  content: '';
  width: 210px;
  height: 300px;
  position: absolute;
  top: 0px;
  right: 0%;
  transform-origin: center;
  transform: rotateY(180deg);
  animation: nextPage 25s -20s infinite steps(1);
  background-size: 420px 300px;
  background-position: 100% -2px;
}
@keyframes nextPage {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
  }
  20% {
    background-image: url('https://picsum.photos/420/300?random=2');
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=3');
  }
  60% {
    background-image: url('https://picsum.photos/420/300?random=4');
  }
  80% {
    background-image: url('https://picsum.photos/420/300?random=5');
  }
}
.gap {
  width: 10px;
  height: 300px;
  background: none;
  transform: rotateX(60deg);
  transform-origin: bottom;
  position: absolute;
  top: 0px;
  left: calc(50% - 5px);
}
.gap::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translate(-50%, 50%);
  background-color: #555;
  width: 10px;
  height: 5px;
  border-radius: 50%;
}
.pages, .flips {
  transform-style: preserve-3d;
}
.flip {
  width: 32px;
  height: 300px;
  position: absolute;
  top: 0px;
  transform-origin: 100% 100%;
  right: 100%;
  border: solid #555;
  border-width: 2px 0px;
  perspective: 4200px;
  perspective-origin: center;
  transform-style: preserve-3d;
  background-size: 420px 300px;
}
.flip::after {
  content: '';
  position: absolute;
  top: 0px;
  right: 0%;
  width: 100%;
  height: 100%;
  transform-origin: center;
  background-size: 420px 300px;
}
.flip.flip1 {
  right: 50%;
  animation: flip1 5s infinite ease-in-out;
  border-width: 2px 2px 2px 0;
}
.flip.flip1::after {
  animation: nextFlip1 25s -20s infinite steps(1);
}
.flip:not(.flip1) {
  right: calc(100% - 2px);
  top: -2px;
  transform-origin: right;
  animation: flip2 5s ease-in-out infinite;
}
.flip.flip2::after {
  animation: nextFlip2 25s -20s infinite steps(1);
}
.flip.flip3::after {
  animation: nextFlip3 25s -20s infinite steps(1);
}
.flip.flip4::after {
  animation: nextFlip4 25s -20s infinite steps(1);
}
.flip.flip5::after {
  animation: nextFlip5 25s -20s infinite steps(1);
}
.flip.flip6::after {
  animation: nextFlip6 25s -20s infinite steps(1);
}
.flip.flip7::after {
  animation: nextFlip7 25s -20s infinite steps(1);
}
.flip.flip7 {
  width: 30px;
  border-width: 2px 0px 2px 2px;
}
.flip.flip7::after {
  animation: nextFlip7 25s -20s infinite steps(1);
}
@keyframes flip1 {
  0%, 20% {
    transform: rotateX(60deg) rotateY(6deg);
  }
  80%, 100% {
    transform: rotateX(60deg) rotateY(174deg);
  }
}
@keyframes flip2 {
  0%, 20% {
    transform: rotateY(0deg) translateY(0px);
  }
  50% {
    transform: rotateY(-15deg) translateY(0px);
  }
}
@keyframes nextFlip1 {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -178px -2px;
    transform: rotateY(0deg);
  }
  10% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -210px -2px;
    transform: rotateY(180deg);
  }
  20% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -178px -2px;
    transform: rotateY(0deg);
  }
  30% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -210px -2px;
    transform: rotateY(180deg);
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -178px -2px;
    transform: rotateY(0deg);
  }
  50% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -210px -2px;
    transform: rotateY(180deg);
  }
  60% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -178px -2px;
    transform: rotateY(0deg);
  }
  70% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -210px -2px;
    transform: rotateY(180deg);
  }
  80% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -178px -2px;
    transform: rotateY(0deg);
  }
  90% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -210px -2px;
    transform: rotateY(180deg);
  }
}
@keyframes nextFlip2 {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -148px -2px;
    transform: rotateY(0deg);
  }
  10.5% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -238px -2px;
    transform: rotateY(180deg);
  }
  20% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -148px -2px;
    transform: rotateY(0deg);
  }
  30.5% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -238px -2px;
    transform: rotateY(180deg);
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -148px -2px;
    transform: rotateY(0deg);
  }
  50.5% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -238px -2px;
    transform: rotateY(180deg);
  }
  60% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -148px -2px;
    transform: rotateY(0deg);
  }
  70.5% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -238px -2px;
    transform: rotateY(180deg);
  }
  80% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -148px -2px;
    transform: rotateY(0deg);
  }
  90.5% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -238px -2px;
    transform: rotateY(180deg);
  }
}
@keyframes nextFlip3 {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -118px -2px;
    transform: rotateY(0deg);
  }
  11% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -268px -2px;
    transform: rotateY(180deg);
  }
  20% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -118px -2px;
    transform: rotateY(0deg);
  }
  31% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -268px -2px;
    transform: rotateY(180deg);
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -118px -2px;
    transform: rotateY(0deg);
  }
  51% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -268px -2px;
    transform: rotateY(180deg);
  }
  60% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -118px -2px;
    transform: rotateY(0deg);
  }
  71% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -268px -2px;
    transform: rotateY(180deg);
  }
  80% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -118px -2px;
    transform: rotateY(0deg);
  }
  91% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -268px -2px;
    transform: rotateY(180deg);
  }
}
@keyframes nextFlip4 {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -88px -2px;
    transform: rotateY(0deg);
  }
  11.5% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -298px -2px;
    transform: rotateY(180deg);
  }
  20% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -88px -2px;
    transform: rotateY(0deg);
  }
  31.5% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -298px -2px;
    transform: rotateY(180deg);
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -88px -2px;
    transform: rotateY(0deg);
  }
  51.5% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -298px -2px;
    transform: rotateY(180deg);
  }
  60% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -88px -2px;
    transform: rotateY(0deg);
  }
  71.5% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -298px -2px;
    transform: rotateY(180deg);
  }
  80% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -88px -2px;
    transform: rotateY(0deg);
  }
  91.5% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -298px -2px;
    transform: rotateY(180deg);
  }
}
@keyframes nextFlip5 {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -58px -2px;
    transform: rotateY(0deg);
  }
  12% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -328px -2px;
    transform: rotateY(180deg);
  }
  20% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -58px -2px;
    transform: rotateY(0deg);
  }
  32% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -328px -2px;
    transform: rotateY(180deg);
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -58px -2px;
    transform: rotateY(0deg);
  }
  52% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -328px -2px;
    transform: rotateY(180deg);
  }
  60% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -58px -2px;
    transform: rotateY(0deg);
  }
  72% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -328px -2px;
    transform: rotateY(180deg);
  }
  80% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -58px -2px;
    transform: rotateY(0deg);
  }
  92% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -328px -2px;
    transform: rotateY(180deg);
  }
}
@keyframes nextFlip6 {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -28px -2px;
    transform: rotateY(0deg);
  }
  12.5% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -358px -2px;
    transform: rotateY(180deg);
  }
  20% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -28px -2px;
    transform: rotateY(0deg);
  }
  32.5% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -358px -2px;
    transform: rotateY(180deg);
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -28px -2px;
    transform: rotateY(0deg);
  }
  52.5% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -358px -2px;
    transform: rotateY(180deg);
  }
  60% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -28px -2px;
    transform: rotateY(0deg);
  }
  72.5% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -358px -2px;
    transform: rotateY(180deg);
  }
  80% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -28px -2px;
    transform: rotateY(0deg);
  }
  92.5% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -358px -2px;
    transform: rotateY(180deg);
  }
}
@keyframes nextFlip7 {
  0% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -2px -2px;
    transform: rotateY(0deg);
  }
  13% {
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -388px -2px;
    transform: rotateY(180deg);
  }
  20%{
    background-image: url('https://picsum.photos/420/300?random=2');
    background-position: -2px -2px;
    transform: rotateY(0deg);
  }
  33% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -388px -2px;
    transform: rotateY(180deg);
  }
  40% {
    background-image: url('https://picsum.photos/420/300?random=3');
    background-position: -2px -2px;
    transform: rotateY(0deg);
  }
  53% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -388px -2px;
    transform: rotateY(180deg);
  }
  60% {
    background-image: url('https://picsum.photos/420/300?random=4');
    background-position: -2px -2px;
    transform: rotateY(0deg);
  }
  73% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -388px -2px;
    transform: rotateY(180deg);
  }
  80% {
    background-image: url('https://picsum.photos/420/300?random=5');
    background-position: -2px -2px;
    transform: rotateY(0deg);
  }
  93% {
    background-image: url('https://picsum.photos/420/300?random=1');
    background-position: -388px -2px;
    transform: rotateY(180deg);
  }
}

/*# sourceMappingURL=main.css.map */
</style>
