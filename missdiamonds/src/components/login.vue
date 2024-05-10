<template @resize="removemenu">
  <div class="hello"  >
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
    <div class="navbar" style="position: -webkit-sticky;  position: sticky; top: 0;  z-index: 5;">
        <div class="container">
            <!-- <a class="logo" href="#">Name</a> -->
            <a  href="https://www.diamondtreats.co.za">
             <img class="logo" href="https://www.diamondtreats.co.za" src="../assets/diamonds.jpg" style="width: 100px; height:50px; "  alt="Open Navigation">
            </a>
            <img @click="addmenu"  class="mobile-menu" src="../assets/menu.svg" alt="Open Navigation">
            <nav id="mysidebar">
                <img @click="removemenu" id="mobile-exit" class="mobile-menu-exit" src="../assets/exit.svg" alt="Close Navigation">
                <ul class="primary-nav">
                  <li class="current"><a @click="removemenu"></a></li>
                </ul>

                <ul class="secondary-nav">
                    <li><a href="https://www.diamondtreats.co.za" >Home</a></li>
                    <li class="go-premium-cta"><a href="https://www.diamondtreats.co.za/#/login">Log in</a></li>
                    <li class="go-premium-cta"><a href="https://www.diamondtreats.co.za/#/signup">Sign up</a></li>
                    <li><a >Contact Us</a></li>
                   <!-- <li class="go-premium-cta"><a href="">Log in</a></li>
                    <li class="d"><a href="">Sign up</a></li> -->
                </ul>
            </nav>
        </div>
    </div>
    <section class="hero2">
        <div class="container">
            <div class="left-col">
               <div class="contact-left">
                <h2>Login</h2>

                <form id="registerid" onsubmit="return false">
                  <div id="suggestions" class="suggestions">
                    <!--<label for="name">Name</label>
                    <input type="text" v-model= "signname" id="name" name="name" required oninvalid="this.setCustomValidity('Enter Name')" oninput="this.setCustomValidity('')">

                    <label for="surname">Surname</label>
                    <input type="text" v-model= "signsurname" id="surname" name="surname" required oninvalid="this.setCustomValidity('Enter Surname')" oninput="this.setCustomValidity('')"> -->

                    <label for="email">Email</label>
                    <input type="email" v-model= "signemail" id="email" name="email" required oninvalid="this.setCustomValidity('Enter Valid Email')" oninput="this.setCustomValidity('')">

                    <label for="password">Password</label>
                    <input type="password" v-model= "signupPass" id="pass" name="pass" required oninvalid="this.setCustomValidity('Passwords don't correspond')" oninput="this.setCustomValidity('')">

                    <!--<label for="conpassword">Confirm Password</label>
                    <input type="password" v-model= "signupPassCon" id="passcon" name="passcon" required oninvalid="this.setCustomValidity('Passwords don't correspond')" oninput="this.setCustomValidity('')"> -->
                    <table style="place-content: space-between;width: 100%;">
                      <tr>
                        <td>
                    <input id="sendesugg" type="button" @click="login"  class="send-message-cta" value="Login" >
                    </td>
                    <td>
                    <input id="sendesugg" type="button" @click="register"  class="send-message-cta" value="Register" >
                    </td>
                    </tr>
                    </table>
                  </div>
                </form>
            </div>
            </div>
        </div>
    </section>
    <div class="feet">
    <h5 style="text-align:center">Copyright © 2024 All Rights Reserved. Designed by <a href="kabelomakganye.co.za">Kabelo</a> </h5>
    </div>

  </div>
</template>

<script>
import logi from '../components/user.vue'
import swal from 'sweetalert'
import FormData from 'form-data'
// import axios from 'axios'
export default {
  components: { 'log-in': logi },
  name: 'HelloWorld',
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
      signemail: '',
      signupPass: '',
      signupPassCon: '',
      pic: null,
      nextpage: '',
      linkdata: 'https://kabelodatabase-4e42dc7fda46.herokuapp.com/'
    }
  },
  mounted () {
    window.addEventListener('resize', this.removemenu)
  },
  /* unmounted () {
    window.removeEventListener('resize', this.removemenu)
  }, */
  methods: {
    async submitFile () {
      const axios = require('axios')
      /*
        Initialize the form data
      */
      let formData = new FormData()
      /*
        Add the form data we need to submit
      */
      formData.append('file', this.file, this.file.name)
      console.log(formData)
      /*
      Make the request to the POST /single-file URL
      */
      await axios.post('http://localhost:3000/uploadpicture', {
        name: formData
      }).then(function () {
        console.log('SUCCESS!!')
      })
        .catch(function () {
          console.log('FAILURE!!')
        })
    },
    handleFileUpload () {
      this.file = this.$refs.file.files[0]
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
    upload (event) {
      // await fetch(`https://kabelodatabase.herokuapp.com/set_pic/${this.$refs.myFiles.files}`)
      this.pic = event.target.files[0]
    },
    async register () {
      window.location.href = 'https://www.diamondtreats.co.za/#/signup'
    },
    async login () {
      let networkcheck = false
      document.getElementById('sendesugg').disabled = true
      document.getElementById('sendesugg').style.backgroundColor = '#F0998B'
      let allAreFilled = true /* check if all required fields are entered */
      document.getElementById('suggestions').querySelectorAll('[required]').forEach(function (i) {
        if (!allAreFilled) return
        if (!i.value) allAreFilled = false
      })
      if (allAreFilled) {
        const axios = require('axios')
        await axios.post(`${this.linkdata}login`, {
          email: this.signemail,
          password: this.signupPass
        })
          .then((response) => {
            /* console.log(response)
            alert(response.data) */
            this.nextpage = response.data
            /* alert(this.nextpage)
            console.log(this.nextpage) */
          }, (error) => {
            console.log(error)
            if (error.message === 'timeout exceeded') {
              // alert('Check your internet connections')
              swal('Check your internet connections', '', 'error')
              networkcheck = true
            }
          })
      } else {
        // alert('fill up everything')
        swal('Fill up everything', '', 'error')
      }
      if (this.nextpage === 'win') {
        await fetch(`${this.linkdata}get_user_miss/${this.signemail}`)
          .then(response => response.json())
          .then(results => (this.resultsFetched_3 = results))
        this.signname = this.resultsFetched_3[0].name_
        this.signsurname = this.resultsFetched_3[0].surname_
        // come back here put all loged in data on cookie
        /* let coo = ''
        let decodedCookie = decodeURIComponent(document.cookie)
        let ca = decodedCookie.split(';')
        for (let i = 0; i < ca.length; i++) {
          let c = ca[i]
          while (c.charAt(0) === ' ') {
            c = c.substring(1)
          }
          if (c.indexOf('userbrajoe=') === 0) {
            coo = c.substring('=', c.length)
            alert(coo)
          }
        }
        if (coo.length <= 1) { */
        const d = new Date()
        d.setTime(d.getTime() + (1 * 1 * 60 * 60 * 1000)) // session will expire after a minute
        // d.setUTCHours(0, 0, 0)
        let expires = 'expires=' + d.toUTCString()
        document.cookie = 'usermissdiamonds' + '=' + this.signname + ';' + expires + ';path=/'
        document.cookie = 'surnamemissdiamonds' + '=' + this.signsurname + ';' + expires + ';path=/'
        document.cookie = 'emailmissdiamonds' + '=' + this.signemail + ';' + expires + ';path=/'
        // add procedure that add to log when one login
        // }
        // window.location.href = 'http://localhost:8080/#/user'
        /* swal('', 'Welcome', 'success', {
          buttons: false,
          timer: 3000
        }) */
        swal('', 'WELCOME', 'success', {
          buttons: false,
          timer: 3000
        })
        // to be done after user page is done
        // window.location.href = 'https://brajoecarwash.co.za/#/user' // 'http://localhost:8080/#/user'
        window.location.href = 'https://www.diamondtreats.co.za/#/user'
      } else if (this.nextpage === 'wrong') {
        // alert('wrong Password')
        swal('wrong Password', '', 'error')
      } else if (networkcheck === false) {
        // alert('invalid user')
        swal('Invalid user', '', 'error')
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
        await axios.post(`${this.linkdata}sendemail`, {
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
<style>
