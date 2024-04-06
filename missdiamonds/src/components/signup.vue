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
                <h2>SignUp</h2>

                <form id="registerid" onsubmit="return false">
                  <div id="suggestions" class="suggestions">
                    <label for="name"><p>Name</p></label>
                    <input type="text" v-model= "signname" id="name" name="name" required oninvalid="this.setCustomValidity('Enter Name')" oninput="this.setCustomValidity('')">

                    <label for="surname">Surname</label>
                    <input type="text" v-model= "signsurname" id="surname" name="surname" required oninvalid="this.setCustomValidity('Enter Surname')" oninput="this.setCustomValidity('')">

                    <!-- <label for="carname">Car Name</label>
                    <input type="text" v-model= "signcarname" id="carname" name="carname" required oninvalid="this.setCustomValidity('Enter Car Name')" oninput="this.setCustomValidity('')">

                    <label for="carreg">Car Registration</label>
                    <input type="text" v-model= "signcarreg" id="carreg" name="carreg" required oninvalid="this.setCustomValidity('Enter registration')" oninput="this.setCustomValidity('')"> -->

                    <label for="number">Cell Number</label>
                    <input type="text" v-model= "signnumber" id="number" name="number" required oninvalid="this.setCustomValidity('Enter Surname')" oninput="this.setCustomValidity('We will contact you if you forget something')">

                    <label for="email">Email</label>
                    <input type="email" v-model= "signemail" id="email" name="email" required oninvalid="this.setCustomValidity('Enter Valid Email')" oninput="this.setCustomValidity('')">

                    <label for="password">Password</label>
                    <input type="password" v-model= "signupPass" id="pass" name="pass" required oninvalid="this.setCustomValidity('Passwords don't correspond')" oninput="this.setCustomValidity('')">

                    <label for="conpassword">Confirm Password</label>
                    <input type="password" v-model= "signupPassCon" id="passcon" name="passcon" required oninvalid="this.setCustomValidity('Passwords don't correspond')" oninput="this.setCustomValidity('')">

                    <input id="sendesugg" type="button" @click="register"  class="send-message-cta" value="Sign Up" >
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
import axios from 'axios'
import swal from 'sweetalert'
export default {
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
      signcarname: 'miss',
      signcarreg: 'miss',
      signemail: '',
      signupPass: '',
      signupPassCon: '',
      signnumber: '',
      pic: null,
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
      axios.post(`${this.linkdata}image`, {
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
          await axios.post(`${this.linkdata}register`, {
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
                this.signcarname = 'miss'
                this.signcarreg = 'miss'
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
