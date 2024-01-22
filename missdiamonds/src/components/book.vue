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
<style>
