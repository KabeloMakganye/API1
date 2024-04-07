<template @resize="removemenu">
  <div class="hello"  @resize="removemenu">
  <div @click="removemenu" class="blur" id="blur"></div>
  <!-- <div @click="removemenu" class="blur2" id="blur2"></div>

  <div class="price">
    <h1 class="price">Prices</h1>
    <ol class="price">
      <li>Saden R60</li>
      <li>Single Cap van</li>
      <li>double Cap van</li>
      <li>Mini budds *Taxi</li>
    </ol>
  </div> -->
    <div class="navbar" style="position: -webkit-sticky;  position: sticky; top: 0;  z-index: 5;">
        <div class="container">
            <!-- <a class="logo" href="#">Name</a> -->
            <a  href="#">
             <img class="logo" href="#" src="../assets/diamonds.jpg" style="width: 100px; height:50px; "  alt="Open Navigation">
            </a>
            <img @click="addmenu"  class="mobile-menu" src="../assets/menu.svg" alt="Open Navigation">
            <nav id="mysidebar">
                <img @click="removemenu" id="mobile-exit" class="mobile-menu-exit" src="../assets/exit.svg" alt="Close Navigation">
                <ul class="primary-nav">
                  <li class="current"><a @click="removemenu"></a></li>
                </ul>

                <ul class="secondary-nav">
                    <li><a >Services</a></li>
                    <li class="go-premium-cta"><a href="https://www.diamondtreats.co.za/#/login">Log in</a></li>
                    <li class="go-premium-cta"><a href="https://www.diamondtreats.co.za/#/signup">Sign up</a></li>
                    <li><a >Contact Us</a></li>
                   <!-- <li class="go-premium-cta"><a href="">Log in</a></li>
                    <li class="d"><a href="">Sign up</a></li> -->
                </ul>
            </nav>
        </div>
    </div>
    <div class="hero">
        <div class="container124">
            <div class="left-col">
               <!-- <p class="subhead">It's Nitty &amp; Gritty</p> -->
               <!-- <h1>Limited OFFER </h1> -->
              <div class="aboutimg1">
                                <h1 style="color: white; text-align: center;vertical-align:bottom">ABOUT US</h1>
                <h2 style="color: white; text-align: center;vertical-align:bottom">We Offer Massage Treats(House Calls Available too) Yoni Virginal Products, Facial glow products, weight-loss & weight-gain products. We are looking forward to building an overlasting business relation with you.</h2>
            </div>
               <!-- <p style="font-size:50px">&#128295;&#128296;&#128297;</p> -->
               <!-- <div class="hero-cta">
                    <a href="#" class="primary-cta">Try for free</a>
                    <a href="#" class="watch-video-cta">
                        <img src="../assets/watch.svg" alt="Watch a video">Watch a video
                    </a>
                </div> -->
            </div>
           <!-- <img src="../assets/108487139-window-wash-1440.jpg" class="hero-img" alt="Illustration">-->
        </div>
    </div>
        <!-- <section class="hero12">
        <div class="container" id ="maindev">
            <div class="left-col">
              <img src="../assets/IMG_2436.jpg" width='100%' class="hero-img2" loading="lazy"  alt="Illustration">
            </DIV>
            <div class="left-col">
              <img src="../assets/IMG_1620.jpg" width='100%' class="hero-img2" loading="lazy"  alt="Illustration">
            </DIV>
            <div class="left-col">
              <img src="../assets/IMG_1348.jpg" width='100%' class="hero-img2" loading="lazy"  alt="Illustration">
            </DIV>
            <div class="left-col">
              <img src="../assets/IMG_1365.jpg" width='100%' class="hero-img2" loading="lazy"  alt="Illustration">
            </DIV>
            <div class="left-col">
              <img src="../assets/IMG_2090.jpg" width='100%' class="hero-img2" loading="lazy"  alt="Illustration">
            </DIV>
            <div class="left-col">
              <img src="../assets/IMG_1621.jpg" width='100%' class="hero-img2" loading="lazy"  alt="Illustration">
            </DIV>
        </div>
    </section>-->
<!-- <div style="text-align:center">
  <span class="dot" @click="currentSlide(1)"></span>
  <span class="dot" @click="currentSlide(2)"></span>
  <span class="dot" @click="currentSlide(3)"></span>
</div> -->
 <!--  <section class="testimonials-section">
        <div class="container">
          <h2>About Us</h2>
          <table >
            <tr >
              <td >
                <img id="app2" class="aboutimg" src="../assets/moritz-kindler-mRBywMReXH8-unsplash.jpg" style="width:100%;display: block;">
              </td>
              <td>
                <p>Our company plays a vital role in the transition to a clean energy future, this is essential part of the renewable energy industry.</p>
              </td>
            </tr>
            <tr >
              <td>
                <p>We offer a wide range of services related to solar energy, including site assessment, system design, installation, and maintenance.</p>
              </td>
              <td>
                <img id="app2" class="aboutimg" src="../assets/alessandro-bianchi-_kdTyfnUFAc-unsplash.jpg" style="width:100%;display: block;">
              </td>
            </tr>
            <tr >
              <td>
                <img id="app2" class="aboutimg" src="../assets/ricardo-gomez-angel-MagdWoazARo-unsplash.jpg" style="width:100%;display: block;">
              </td>
              <td >
                <p >Our primary goal is to help our customers transition to clean, renewable energy sources and reduce their carbon footprint. By providing high-quality solar systems that generate electricity from the sun's rays. This can help customers reduce their reliance on Eskom.</p>
              </td>
            </tr>
          </table>

        </div>
    </section>

    <section class="testimonials-section2">
        <div class="container">
          <h2>Services</h2>
            <div class="navbardown">
              <div class="aboutimg" style="background-color: rgb(255,255,255);">
                <table style="width:100%;">
                  <tr>
              <td >
                <img id="app2" src="../assets/alternative-clean-green-energy-sustainability-concept-photovoltaic-solar-panel-plant-leaves-sun-isolated-white-background-182932636.jpg" style="width:100%;display: block;">
              </td>
              </tr>
              </table>
              <table style="width: 100%;">
                <tr>
              <th>
                <p style="color: black;text-align: center;vertical-align:bottom">Up to 4 Hours lights and part of entertaiment systems.</p>
              </th>
            </tr>
            <tr>
              <th>
                <h3 style="color: black;text-align: center;vertical-align:bottom">From R10 000.00</h3>
              </th>
            </tr>
              </table>
            </div>

              <div class="aboutimg" style="background-color: rgb(88,106,105);">
                <table style="width:100%;">
                  <tr>
              <td>
                <img id="app2"  src="../assets/thumbnail_Get_More_For_Their_Solar-03.png" style="width:100%;display: block;">
              </td>
              </tr>
              </table>
              <table style="width: 100%;">
                <tr>
              <th>
                <p style="color: black;text-align: center;vertical-align:bottom">Up to 8 Hours lights and entertaiment systems.</p>
              </th>
            </tr>
            <tr>
              <th>
                <h3 style="color: black;text-align: center;vertical-align:bottom">From R25 000.00</h3>
              </th>
            </tr>
              </table>
              </div>
              <div class="aboutimg" style="background-color: rgb(169,160,121);">
                <table style="width:100%;">
                  <tr>
              <th>
                <img id="app2"  src="../assets/2f757227fcd3a40558e9c4853e8e06c-1024x576.jpg" style="width:100%;display: block;">
              </th>
            </tr>
            </table>
            <table style="width: 100%;">
              <tr>
                <th>
                  <p style="color: black;text-align: center;vertical-align:bottom">Full house off the grid</p>
                </th>
              </tr>
            <tr>
              <th >
                <h3  style="color: black;text-align: center;vertical-align:bottom">From R50 000.00</h3>
              </th>
            </tr>
              </table>
            </div>
          </div>

        </div>
    </section>-->
    <!-- BOOKING ON HOME PAGE -->
    <!-- <section id="book2" class="testimonials-section">
        <div class="container">
            <div class="left-col">
                <h2>Book Now</h2>

                <form id="registerid" onsubmit="return false">
                  <div id="suggestions2" class="suggestions2">

                    <input  type= "date" class="aboutimg3" id="myDate" v-model="date_" min="2022-11-26" max="2022-11-26" required pattern="\d{4}-\d{2}-\d{2}"> <br>
                    <input  type= "time" class="aboutimg3" id="myDate2" v-model="date_" step="900" required pattern="[0-1][0-3]:[0-5][0-9]"><br>

                    <input id="sendesugg"  type="submit" @click="bookdate"  class="send-message-cta" value="Save" >
                  </div>
                </form>
            </div>
        </div>
    </section> -->
    <!--
   <section class="testimonials-section">
        <div class="container">
                        <div class="aboutimg">
              <table style="width: 100%;">
                <tr>
              <th>
                <p style="text-align: center;vertical-align:bottom">We Offer Massage Treats(House Calls Available too) Yoni Virginal Products, Facial glow products, weight-loss & weight-gain products. We are looking forward to building an overlasting business relation with you.</p>
              </th>
            </tr>
            <tr>
            </tr>
              </table>
            </div>
          <table >
            <tr>
              <td>
                <img id="app2" class="aboutimg" src="../assets/d5.jpg" style="width:100%;display: block;">
              </td>
              <td>
                <p>Your Comfort is our priority</p>
              </td>
            </tr>
            <tr >
              <td>
                <p>Your Comfort is our priority</p>
              </td>
              <td>
                <img id="app2" class="aboutimg" src="../assets/d6.jpg" style="width:100%;display: block;">
              </td>
            </tr>
            <tr >
              <td>
                <img id="app2" class="aboutimg" src="../assets/d9.jpg" style="width:100%;display: block;">
              </td>
              <td >
                <p >Payment methods</p>
              </td>
            </tr>
          </table>

        </div>
    </section> -->

    <div class="abc"></div>
    <section>
                        <div class="contact-left">
                       <!-- <div class="aboutimg">
                <h2 style="text-align: center;vertical-align:bottom">We Offer Massage Treats(House Calls Available too) Yoni Virginal Products, Facial glow products, weight-loss & weight-gain products. We are looking forward to building an overlasting business relation with you.</h2>
            </div> -->
        <div class="container">

          <table >
            <!-- <tr>
                  <img id="app2" src="../assets/d1.jpg"  class="aboutimg123" style="right: 50%; width:100%;display: block;">
                  <img id="app2" src="../assets/d2.jpg"  class="aboutimg123" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d3.jpg"  class="aboutimg123" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d4.jpg"  class="aboutimg123" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d5.jpg"  class="aboutimg123" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d6.jpg"  class="aboutimg123" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d7.jpg"  class="aboutimg123" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d8.jpg"  class="aboutimg123" style="right: 50%; width:100%;display: none;">
            </tr> -->
            <tr>
              <td>
                <img id="app2" class="aboutimg" src="../assets/d5.jpg" style="width:100%;display: block;">
              </td>
              <td>
                <p>Your Comfort is our priority</p>
              </td>
            </tr>
            <tr >
              <td>
                <p>Your Comfort is our priority</p>
              </td>
              <td>
                <img id="app2" class="aboutimg" src="../assets/d6.jpg" style="width:100%;display: block;">
              </td>
            </tr>
            <tr >
              <td>
                <img id="app2" class="aboutimg" src="../assets/d9.jpg" style="width:100%;display: block;">
              </td>
              <td >
                <p >Payment methods</p>
              </td>
            </tr>
          </table>
        </div>
            </div>
                        <div class="contact-left">
              <h2>OUR GALARY AND SPECIALS</h2>
                  <img id="app2" src="../assets/d1.jpg"  class="aboutimg1234" style="right: 50%; width:100%;display: block;">
                  <img id="app2" src="../assets/d2.jpg"  class="aboutimg1234" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d3.jpg"  class="aboutimg1234" style="right: 50%; width:100%;display: none;">
                  <!-- <img id="app2" src="../assets/d4.jpg"  class="aboutimg1234" style="right: 50%; width:100%;display: none;"> -->
                  <img id="app2" src="../assets/d5.jpg"  class="aboutimg1234" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d6.jpg"  class="aboutimg1234" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d7.jpg"  class="aboutimg1234" style="right: 50%; width:100%;display: none;">
                  <img id="app2" src="../assets/d8.jpg"  class="aboutimg1234" style="right: 50%; width:100%;display: none;">
            </div>

        <div class="container">
            <div class="contact-left">
              <h2>CONTACT US</h2>
              <!--<div class="aboutimg2"> -->
                <!--<h2 class="abc" style=" text-align: center;">CONTACT US</h2> -->
                <!-- <h3 style="text-align: center; color: white;">RESIDENTIAL | COMMERTIAL | CUSTOM INSTALLS </h3>
                <p style=" text-align: center; color: white;">Submit your information and we will give you a call</p> -->
              <!-- </div> -->

                <form onsubmit="return false">
                  <div id="suggestions" class="suggestions">
                    <input class="aboutimg3" type="text" v-model= "sugname" placeholder="Name" id="name" name="name" required oninvalid="this.setCustomValidity('Enter Name')" oninput="this.setCustomValidity('')">

                    <input class="aboutimg3" type="email" v-model= "sugemail" placeholder="Email" id="email" name="email" required oninvalid="this.setCustomValidity('Enter Valid Email')" oninput="this.setCustomValidity('')">
                    <input class="aboutimg3" type="phone" v-model= "sugphone" placeholder="Phone" id="phone" name="phone" required oninvalid="this.setCustomValidity('Enter Phone)" oninput="this.setCustomValidity('')">
                    <textarea class="aboutimg3" style="resize: none;" name="message" placeholder="Short description" v-model= "sugmessage" id="message" cols="30" rows="10" required oninvalid="this.setCustomValidity('Enter Suggestion message')" oninput="this.setCustomValidity('')"></textarea>

                    <input  id="sendesugg" type="button" @click="sendemail" class="send-message-cta aboutimg3" value="SEND">
                  </div>
                </form>
                <p></p>
            </div>
        </div>

    </section>
        <div class="mappp">
                                  <div class="contact-left2">
              <h2>OUR LOCATION</h2>
              <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d560.9759127354943!2d27.978915963662324!3d-25.61351679778013!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1ebfd27b0c2b0abd%3A0x156aea99e00dc420!2s6002%20Maseloane%20St%2C%20Ga-Rankuwa%20Zone%201%2C%20Ga-Rankuwa%2C%200208!5e1!3m2!1sen!2sza!4v1705666033163!5m2!1sen!2sza" width="100%" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
            </div>

        </div>
<!-- <div >
<iframe src="https://travelsakireminder.web.app/#/signup" width="600" height="800px" scrolling="no" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
</div> -->
            <div class="foots">
    <app-footer/>
    </div>
  </div>
</template>
<script>
import foot from './foot.vue'
import axios from 'axios'
import swal from 'sweetalert'
export default {
  components: {'app-footer': foot},
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      file: '1111',
      sugname: '',
      sugemail: '',
      sugphone: '',
      sugmessage: '',
      resultsFetched_3: '',
      atload: 0,
      pictures: [],
      picturesby: [],
      picturelimit: 0,
      n: '',
      slideIndex: 1,
      time: '',
      linkdata: 'https://kabelodatabase-4e42dc7fda46.herokuapp.com/'
    }
  },

  /* unmounted () {
    window.removeEventListener('resize', this.removemenu)
  }, */
  methods: {
    bookdate () {
      let allAreFilled = true /* check if all required fields are entered */
      document.getElementById('suggestions2').querySelectorAll('[required]').forEach(function (i) {
        if (!allAreFilled) return
        if (!i.value) allAreFilled = false
      })
      if (allAreFilled) {
        swal('Quote Sent', '', 'success', {
          buttons: false,
          timer: 3000
        })
      }
    },
    directto (n) {
      window.location.href = `https://solarinstalls.web.app/#/${n}` // `http://localhost:8080/#/${n}`
      // window.location.href = `http://localhost:8080/#/${n}`
    },
    showSlides (n) {
      let i
      let slides = document.getElementsByClassName('aboutimg1234')
      // let dots = document.getElementsByClassName('dot')
      if (n > slides.length) { this.slideIndex = 1 }
      if (n < 1) { this.slideIndex = slides.length }
      for (i = 0; i < slides.length; i++) {
        slides[i].style.display = 'none'
      }
      /* for (i = 0; i < dots.length; i++) {
        dots[i].className = dots[i].className.replace(' active', '')
      } */
      slides[this.slideIndex - 1].style.display = 'block'
      // dots[this.slideIndex - 1].className += ' active'
    },
    clearIntervals () {
      clearInterval(this.time)
      this.time = setInterval(() => this.plusSlides(1), 10000)
    },
    plusSlides (n) {
      this.showSlides(this.slideIndex += n)
    },
    currentSlide (n) {
      this.showSlides(this.slideIndex = n)
    },
    setp (n) {

    },
    direct () {
      window.location.href = 'https://kabelodatabase.herokuapp.com'
    },
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
    async upload () {
      await fetch(`https://kabelodatabase.herokuapp.com/set_pic/${this.$refs.myFiles.files}`)
      console.log(this.$refs.myFiles.files)
    },
    async register () {
      // const axios = require('axios')
      // console.log(others.Axios.length)
      axios.post('https://kabelodatabase.herokuapp.com/register', {
        todo: 'Buy the milk'
      })
        .then((response) => {
          console.log(response)
          alert(response.data)
        }, (error) => {
          console.log(error)
        })
    },
    async sendemail () {
      document.getElementById('sendesugg').disabled = true
      document.getElementById('sendesugg').style.backgroundColor = 'rgba(45, 62, 80, 0.274)'
      let allAreFilled = true /* check if all required fields are entered */
      document.getElementById('suggestions').querySelectorAll('[required]').forEach(function (i) {
        if (!allAreFilled) return
        if (!i.value) allAreFilled = false
      })
      if (allAreFilled) {
        // const axios = require('axios')
        // await axios.post('http://localhost:3000/sendemailmissdiamonds', {
        await axios.post(`${this.linkdata}sendemailmissdiamonds`, {
          sugestionname: this.sugname,
          sugestionmessage: this.sugmessage,
          sendereamil: 'missdiamondswebsite@gmail.com',
          sugemail: this.sugemail,
          sugphone: this.sugphone
        })
          .then((response) => {
            this.sugname = ''
            this.sugmessage = ''
            this.sugemail = ''
            this.sugphone = ''
            // console.log(response)
            swal('Message Sent, We will be in touch.', '', 'success', {
              buttons: false,
              timer: 3000
            })
            // alert(response.data)
          }, (error) => {
            console.log(error)
            swal('Please use Whatsapp', '', 'error')
          })
      } else {
        swal('Enter all required fields', '', 'erroheror')
      }
      document.getElementById('sendesugg').disabled = false
      document.getElementById('sendesugg').style.backgroundColor = '#2D3E50'
      /* await fetch(`https://kabelodatabase.herokuapp.com/sendemail/joesdrivethrough@gmail.com/` + this.sugname + ' ' + this.sugmessage)
          .then(response => response.json())
          .then(results => (this.resultsFetched_3 = results))
        alert(this.resultsFetched_3)
      } */
    },
    async count () {
      await fetch(`https://kabelodatabase-4e42dc7fda46.herokuapp.com/fn_add_load/missdiamonds`)
    },
    rerun () {
      this.time = setInterval(() => this.plusSlides(1), 10000)
    },
    fixdate () {
      var d = new Date()
      var dmax = new Date()
      d.setTime(d.getTime())
      dmax.setTime(dmax.getTime() + (360 * 24 * 60 * 60 * 1000))
      var month = d.getMonth() + 1
      var year = d.getFullYear()
      var day = d.getDate()

      var maxmonth = dmax.getMonth() + 1
      var maxyear = dmax.getFullYear()
      var maxday = dmax.getDate()
      if (month < 10) {
        if (day < 10) {
          document.getElementById('myDate').min = year + '-0' + month + '-0' + day
        } else {
          document.getElementById('myDate').min = year + '-0' + month + '-' + day
        }
      } else {
        if (day < 10) {
          document.getElementById('myDate').min = year + '-' + month + '-0' + day
        } else {
          document.getElementById('myDate').min = year + '-' + month + '-' + day
        }
      }

      if (maxmonth < 10) {
        if (maxday < 10) {
          document.getElementById('myDate').max = maxyear + '-0' + maxmonth + '-0' + maxday
        } else {
          document.getElementById('myDate').max = maxyear + '-0' + maxmonth + '-' + maxday
        }
      } else {
        if (maxday < 10) {
          document.getElementById('myDate').max = maxyear + '-' + maxmonth + '-0' + maxday
        } else {
          document.getElementById('myDate').max = maxyear + '-' + maxmonth + '-' + maxday
        }
      }
    }
  },
  beforeMount () {
    this.rerun()
  },
  mounted () {
    // this.loadpictures()
    window.addEventListener('resize', this.removemenu)
    // create a cookie that will help us coont number of page visits.
    let coo = ''
    let decodedCookie = decodeURIComponent(document.cookie)
    let ca = decodedCookie.split(';')
    for (let i = 0; i < ca.length; i++) {
      let c = ca[i]
      while (c.charAt(0) === ' ') {
        c = c.substring(1)
      }
      if (c.indexOf('logsmissdiamonds=') === 0) {
        coo = c.substring('logsmissdiamonds=', c.length)
      }
    }
    if (coo.length <= 1) {
      this.count()
      const d = new Date()
      d.setTime(d.getTime() + (1 * 24 * 60 * 60 * 1000))
      d.setUTCHours(0, 0, 0)
      let expires = 'expires=' + d.toUTCString()
      document.cookie = 'logsmissdiamonds' + '=' + 'diamonds' + ';' + expires + ';path=/'
    }
    this.showSlides(this.slideIndex)
    this.fixdate()
  }
}
</script>
<!-- /GetButton.io widget -->
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
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
  background-color: rgb(202,203,159);
  /* box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19); */
  box-shadow: 0 4px 8px 0 rgba(255, 242, 0, 0.2), 0 6px 20px 0 rgba(255, 242, 0, 0.19);
  margin-bottom: 25px;
  padding-left: 10px;
  padding-top: 10px;
  padding-right: 10px;
  padding-bottom: 10px;
  border-radius: 25px;
}
.aboutimg3 {
  color: rgb(137, 133, 19);
  background-color: rgb(202,203,159);
  /* box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19); */
  box-shadow: 0 4px 8px 0 rgba(255, 242, 0, 0.2), 0 6px 20px 0 rgba(255, 242, 0, 0.19);
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
p{
  font-family: 'Josefin Slab', serif;
  color: black;
}

body {
  background: rgba(133, 129, 5, 0.172);  /*rgb(242,246,249);/* rgba(0, 0, 0, 100); */
  margin: 0;
  font-family: 'Poppins';
}

.navbar {
  background: rgb(242,246,249); /* black; */
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
  color: black;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

section {
  padding: 0em 2em;
}
.mappp {
  padding: 0em 0em;
}

.container124 {
  /* text-align: center; */
      background:url('../assets/home2.jpg');
     /* background-image-opacity: 0.2; */
      background-repeat: no-repeat;
  background-attachment: scroll;
  background-position: center;
  background-size: 200%;
  height: 100%;
      padding: 5em 2em 5em 2em;
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
 /* line-height: 1.3em;
  margin-top: .2em; */
  color: #000000;
}

.left-col .primary-cta {
  background: var(--primary-color);
  color: white;
  text-decoration: none;
  /* padding: .6em 1.3em; */
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
  background: rgba(133, 129, 5, 0.37); /* var(--primary-color); */
  color: white;
  padding: 1em 1em;
}
.testimonials-section2 {
  background: rgba(109, 104, 104, 0.2);
  color: white;
  padding: 1em 1em;
}

.testimonials-section li {
    color: rgb(0, 0, 0);
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
    .contact-left2 {
    position: relative;
    left: 0%;
    top: 0;
    width: 100%;
    height: 100%;
  }
.testimonials-section li img {
 /* width: 5em;
  height: 5em;
  border: 5px solid #006BD6;
  border-radius: 50%;
  margin-top: -4.5em; */
}

label {
  display: block;
  font-size: 1.2em;
  margin-bottom: .5em;
}

.userinput, input, textarea {
  width: 100%;
  padding: .8em;
  margin-bottom: 1em;
  border-radius: .3em;
  border: 1px solid rgb(45,62,80);
  -webkit-box-sizing: border-box;
          box-sizing: border-box;
}

input[type="date"] {
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
  box-shadow: 0 4px 8px 0 rgba(255, 242, 0, 0.2), 0 6px 20px 0 rgba(255, 242, 0, 0.19);
}

input[type="submit"] {
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
  box-shadow: 0 4px 8px 0 rgba(255, 242, 0, 0.2), 0 6px 20px 0 rgba(255, 242, 0, 0.19);
}

iframe {
  width: 100%;
  height: 300px;
  /* box-shadow: 0 4px 8px 0 rgba(255, 242, 0, 0.2), 0 6px 20px 0 rgba(255, 242, 0, 0.19); */
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
  background:  rgba(193, 193, 193, 0.9);
  height: 100vh;
  padding: 1em;
}

nav ul.primary-nav {
  margin-top: 5em;
}
  .aboutimg123 {
    position: relative;
    left: 40%;
    top: 0;
    width: 100%;
    height: 100%;
      box-shadow: 0 4px 8px 0 rgba(255, 242, 0, 0.2), 0 6px 20px 0 rgba(255, 242, 0, 0.19);
 margin-bottom: 25px;
  }
    .aboutimg1234 {
      box-shadow: 0 4px 8px 0 rgba(255, 242, 0, 0.2), 0 6px 20px 0 rgba(255, 242, 0, 0.19);
 margin-bottom: 25px;
  }

nav li a {
  color: black;
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
  h2 {
  color: black;
  text-decoration: none;
  display: block;
  padding: .5em;
  font-size: 1em;
  text-align: center;
font-family: 'Preahvihear', sans-serif;
}
  input, select, textarea {
    font-size: 16px;
  }
  .navbar nav li.current a {
    color: rgb(0, 0, 0);
  }
    .hero .container .left-col {
    margin: 0em 0em 0em 0em;
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
    color: rgb(0, 0, 0);
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
    h2 {
  color: black;
  text-decoration: none;
  display: block;
  padding: .5em;
  font-size: 2em;
  text-align: center;
font-family: 'Preahvihear', sans-serif;
}
  .container {
    width: 100%;
    margin: 0 auto;
  }
  section {
    padding: 0em 0em;
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
    margin: 5em 5em 5em 5em;
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
      width: 100%;
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
    /*border: 15px;
    margin: 0em 0em 0 0em;
    background: rgba(255, 255, 255, 0.05);
     backdrop-filter: blur(8px);*/
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
  color: rgb(0, 0, 0);
  text-decoration: none;
  display: block;
  padding: .5em;
  font-size: 1em;
  text-align: left;
font-family: 'Preahvihear', sans-serif;
}
label {
  color: rgb(0, 0, 0);
  text-decoration: none;
  display: block;
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
    color:rgb(206, 203, 179);
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
.swal-overlay {
  background-color: rgba(189, 34, 34, 0.383)
}
.swal-modal {
  background-color: rgb(255, 255, 255);
  border: 3px solid white;
}
</style>
