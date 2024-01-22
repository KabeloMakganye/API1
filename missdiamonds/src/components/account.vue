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
      <li>Mini bus *Taxi</li>
    </ol>
  </div> -->
    <div class="navbar">
        <div class="container">
        <a class="logo" href="https://brajoecarwash.co.za/#/">BRA JOE<span> CarWash</span></a>
            <img @click="addmenus"  class="mobile-menu" src="../assets/menu.svg" alt="Open Navigation">
            <nav id="mysidebar">
                <img @click="removemenu" id="mobile-exit" class="mobile-menu-exit" src="../assets/exit.svg" alt="Close Navigation">
                <ul class="primary-nav">
                    <!-- <li><a class="logo"><span>{{signname}}</span></a></li>
                    <li class="current"><a href="https://brajoecarwash.co.za/#/">Home</a></li>
                    <li><a @click="todash()">Dashboard</a></li> -->

                </ul>

                <ul class="secondary-nav">
                    <li><a class="logo"><span>{{signname}}</span></a></li>
                    <li class="current"><a href="https://brajoecarwash.co.za/#/">Home</a></li>
                    <li><a @click="todash()">Dashboard</a></li>
                    <li><a href="#">Contact</a></li>
                    <li class="go-premium-cta"><a @click="logout">Logout</a></li>
                </ul>
            </nav>
        </div>
    </div>

    <section class="heros">
        <div class="container">
            <div class="left-col">
               <!-- <p class="subhead">It's Nitty &amp; Gritty</p> -->
               <h1>Account </h1>
                <blockquote>{{signname}}</blockquote>
                <blockquote>{{signsurname}}</blockquote>
               <!-- <p style="font-size:50px">&#128295;&#128296;&#128297;</p> -->
               <!-- <div class="heros-cta">
                    <a href="#" class="primary-cta">Try for free</a>
                    <a href="#" class="watch-video-cta">
                        <img src="../assets/watch.svg" alt="Watch a video">Watch a video
                    </a>
                </div> -->
            </div>
           <!-- <img src="../assets/108487139-window-wash-1440.jpg" class="heros-img" alt="Illustration">-->
        </div>
    </section>

    <section class="testimonials-section">
        <div class="container">
            <!--<ul>
                <li>
                    <img src="../assets/kb.jpg" alt="Person">

                    <blockquote>"Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore"</blockquote>
                    <cite>- Jane Doe</cite>
                </li>
                <li>
                    <img src="../assets/kb.jpg" alt="Person">

                    <blockquote>"Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore"</blockquote>
                    <cite>- Jane Doe</cite>
                </li>
                <li>
                    <img src="../assets/kb.jpg" alt="Person">

                    <blockquote>"Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore"</blockquote>
                    <cite>- Jane Doe</cite>
                </li>
            </ul> -->
        </div>
    </section>
        <div class="feet">
    <h5 style="text-align:center">Copyright © 2023 All Rights Reserved. Designed by <a href="">car wash</a> </h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'account',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      file: '1111',
      sugname: '',
      sugemail: '',
      sugmessage: '',
      resultsFetched_3: '',
      atload: 0,

      signname: '',
      signsurname: '',
      nextpages: '',
      linkdata: 'https://kabelodatabase-4e42dc7fda46.herokuapp.com/'
    }
  },

  unmounted () {
    window.removeEventListener('resize', this.removemenu)
  },
  methods: {
    checksession () {
      if (this.getCookie('userbrajoe') === 'none') {
        alert('Session expired, login again')
        // window.location.replace('http://localhost:8080/#/login')
        window.location.replace('https://brajoecarwash.co.za/#/login')
      } else {
        const d = new Date()
        d.setTime(d.getTime() + (1 * 1 * 1 * 1 * 180000)) // session will expire after a minute
        // d.setUTCHours(0, 0, 0)
        let expires = 'expires=' + d.toUTCString()
        document.cookie = 'userbrajoe' + '=' + this.signname + ';' + expires + ';path=/'
        document.cookie = 'surnamebrajoe' + '=' + this.signsurname + ';' + expires + ';path=/'
        document.cookie = 'emailbrajoe' + '=' + this.signemail + ';' + expires + ';path=/'
      }
    },
    logout () {
      const d = new Date()
      d.setTime(d.getTime() - (1 * 1 * 1 * 1 * 180000)) // session will expire after a minute
      // d.setUTCHours(0, 0, 0)
      let expires = 'expires=' + d.toUTCString()
      document.cookie = 'userbrajoe' + '=' + this.signname + ';' + expires + ';path=/'
      document.cookie = 'surnamebrajoe' + '=' + this.signsurname + ';' + expires + ';path=/'
      document.cookie = 'emailbrajoe' + '=' + this.signemail + ';' + expires + ';path=/'
      // add procedure that add to log when one login
      // }
      // window.location.replace('http://localhost:8080/#/login')
      window.location.replace('https://brajoecarwash.co.za/#/login')
    },
    getCookie (cname) {
      let name = cname + '='
      let decodedCookie = decodeURIComponent(document.cookie)
      let ca = decodedCookie.split(';')
      for (let i = 0; i < ca.length; i++) {
        let c = ca[i]
        while (c.charAt(0) === ' ') {
          c = c.substring(1)
        }
        if (c.indexOf(name) === 0) {
          return c.substring(name.length, c.length)
        }
      }
      return 'none'
    },
    todash () {
      this.checksession() // if cookies expired it logout
      window.location.href = 'https://brajoecarwash.co.za/#/user'
    },
    removemenu () {
      document.getElementById('blur').style.width = '0%'
      document.querySelector('nav').classList.remove('menu-btn')
    },
    addmenus () {
      document.querySelector('nav').classList.add('menu-btn')
      document.getElementById('blur').style.width = '100%'
    },
    async counts () {
      await fetch(`${this.linkdata}fn_add_load/brajoe`)
    }
  },
  mounted () {
    window.addEventListener('resize', this.removemenu)
    if (this.getCookie('userbrajoe') === 'none') {
      alert('Session expired, login again')
      // window.location.replace('http://localhost:8080/#/login')
      window.location.replace('https://brajoecarwash.co.za/#/login') // 'http://localhost:8080/#/login'
    } else {
      this.signname = this.getCookie('userbrajoe')
      this.signsurname = this.getCookie('surnamebrajoe')
      this.signemail = this.getCookie('emailbrajoe')
    }
    // alert('welcome')
    // create a cookie that will help us coont number of page visits.
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
