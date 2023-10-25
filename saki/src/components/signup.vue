<template @resize="removemenu">
<div >
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
<img class="ppp" src="../assets/slide2.jpg" alt=''>
<img class="ppp" src="../assets/slide3.jpg" alt=''>
<img class="ppp" src="../assets/slide4.jpg" alt=''>
<img class="ppp" src="../assets/slide5.jpg" alt=''>
<img class="ppp" src="../assets/slide6.jpg" alt=''>
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
<img class="ppp" src="../assets/IMG-20230216-WA0070.jpg" alt=''>
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
:root {
--duration: 20s;
--delay: 20s;
}
.ppp {
--duration: 40s;
--name: float-up-1;
position: absolute;
top: 0;
left: 0;
width: 33vw;
transform: translateY(200vh);
animation: var(--name) var(--duration) linear infinite;
box-shadow: 1px 3px 15px rgba(0, 0, 0, 0.5);
z-index: 1;
}
 .ppp:nth-child(1) {
animation-delay: 0s;
}
 .ppp:nth-child(2) {
animation-delay: -3s;
}
 .ppp:nth-child(3) {
animation-delay: -6s;
}
 .ppp:nth-child(4) {
animation-delay: -9s;
}
 .ppp:nth-child(5) {
animation-delay: -12s;
}
 .ppp:nth-child(6) {
animation-delay: -15s;
}
 .ppp:nth-child(7) {
animation-delay: -18s;
}
.ppp:nth-child(8) {
animation-delay: -21s;
}
.ppp:nth-child(9) {
animation-delay: -24s;
}
 .ppp:nth-child(10) {
animation-delay: -27s;
}
.ppp:nth-child(1) {
--name: float-up-1;
--duration: calc(20s * 1);
left: 0vw;
z-index: -1;
}
.ppp:nth-child(2) {
--name: float-up-3;
--duration: calc(20s * 3);
left: 10vw;
z-index: -3;
}
.ppp:nth-child(3) {
--name: float-up-2;
--duration: calc(20s * 2);
left: 90vw;
z-index: -2;
}
 .ppp:nth-child(4) {
--name: float-up-1;
--duration: calc(20s * 1);
left: 36vw;
z-index: -1;
}
 .ppp:nth-child(5) {
--name: float-up-3;
--duration: calc(20s * 3);
left: 62vw;
z-index: -3;
}
 .ppp:nth-child(6) {
--name: float-up-2;
--duration: calc(20s * 2);
left: 15vw;
z-index: -2;
}
 .ppp:nth-child(7) {
--name: float-up-2;
--duration: calc(20s * 2);
left: 55vw;
z-index: -2;
}
 .ppp:nth-child(8) {
--name: float-up-3;
--duration: calc(20s * 3);
left: -20vw;
z-index: -3;
}
 .ppp:nth-child(9) {
--name: float-up-1;
--duration: calc(20s * 1);
left: 68vw;
z-index: -1;
}
.ppp:nth-child(10) {
--name: float-up-2;
--duration: calc(20s * 2);
left: 0vw;
z-index: -2;
}
@keyframes float-up-3 {
from {
transform: translateY(200vh) translateZ(-50vh);
}
to {
transform: translateY(-200vh) translateZ(-50vh);
}
}
@keyframes float-up-2 {
from {
transform: translateY(150vh) translateZ(-25vh);
}
to {
transform: translateY(-150vh) translateZ(-25vh);
}
}
@keyframes float-up-1 {
from {
transform: translateY(100vh);
}
to {
transform: translateY(-100vh);
}
}
/*# sourceMappingURL=main.css.map */
</style>
