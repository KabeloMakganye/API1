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
            <a  href="#">
             <img class="logo" href="https://www.diamondtreats.co.za" src="../assets/diamonds.jpg" style="width: 100px; height:50px; "  alt="Open Navigation">
            </a>
            <img @click="addmenus"  class="mobile-menu" src="../assets/menu.svg" alt="Open Navigation">
            <nav id="mysidebar">
                <img @click="removemenu" id="mobile-exit" class="mobile-menu-exit" src="../assets/exit.svg" alt="Close Navigation">
                <ul class="primary-nav">
                    <li class="current"><a href="https://www.diamondtreats.co.za/#/">Home</a></li>
                    <!--<li><a @click="toaccount()">Account</a></li>-->

                </ul>

                <ul class="secondary-nav">
                  <!-- <input id="sendesuggs" type="button" @click="direct" class="send-message-cta" value="Upload Image"> -->
                   <li><a>{{signname}}</a></li>
                    <li><a @click="direct" href="#">Upload Image</a></li>
                    <!-- <li><a @click="directto('profile')">Profile</a></li> -->
                    <!-- <li><a href="#">Contact</a></li> -->
                    <!-- <li id="homebooking" ><a  @click="history(2)">History</a></li>
                    <li id="infodata" style="display: none;"><a  @click="history(1)">add wash</a></li> -->
                    <li class="go-premium-cta"><a @click="logout">Logout</a></li>
                </ul>
            </nav>
        </div>
    </div>

      <section class="hero2">
        <div class="container">
            <div class="left-col">
              <div class="contact-left">
               <!-- <p class="subhead">It's Nitty &amp; Gritty</p> -->
               <!-- <h1>Limited OFFER </h1> -->
                <!-- <h2>{{signname}}</h2> -->
                <h2>You have {{points}} Points</h2>
                <form id="registerid" onsubmit="return false">
                  <div id="suggestions" class="suggestions">
                    <h2>BOOK NOW...!</h2>

                    <label for="date">Choose Plan</label>
                    <select @mouseleave="shownumberofpeople()" @change="shownumberofpeople()" @click="shownumberofpeople()" required oninvalid="this.setCustomValidity('Choose plan')" oninput="this.setCustomValidity('')" class="userinput" id="cars" name="cars" v-model="selectedcar">
                      <option value="" disabled selected hidden  >Choose Plan</option>
                      <option @click="shownumberofpeople()" v-for="n in packagecount" :key= "n">{{ signcarname[n-1] }}</option>
                    </select><br>

                    <div id="enternumberofpeople">
                    <label for="email">Number of People</label>
                    <input type="number" v-model= "visitors" id="visitors" name="visitors" required oninvalid="this.setCustomValidity('Enter Number Of People')" oninput="this.setCustomValidity('')">
                    </div>

                    <label for="date">Choose Date</label>
                    <input type= "date" id="myDate" v-model="date_" max="2050-11-26" required pattern="\d{4}-\d{2}-\d{2}"> <br>

                    <label for="date">Choose Time Slot</label>
                    <select required oninvalid="this.setCustomValidity('Enter Number Of People')" oninput="this.setCustomValidity('')" class="userinput" id="cars" name="cars" v-model="selectedtime">
                      <option  value="" disabled selected hidden  >Available Slots</option>
                      <option v-for="n in timeslotscount" :key= "n">{{ slots[n-1] }}</option>
                    </select><br>
                    <input id="sendesugg" type="button" @click="addbooking"  class="send-message-cta" value="Save" >
                  </div>
                </form>
                <!--<blockquote>{{signsurname}}</blockquote>-->
               <!-- <p style="font-size:50px">&#128295;&#128296;&#128297;</p> -->
               <!-- <div class="heros-cta">
                    <a href="#" class="primary-cta">Try for free</a>
                    <a href="#" class="watch-video-cta">
                        <img src="../assets/watch.svg" alt="Watch a video">Watch a video
                    </a>
                </div> -->
              </div>
            </div>
           <!-- <img src="../assets/108487139-window-wash-1440.jpg" class="heros-img" alt="Illustration">-->
        </div>
    </section>

    <!-- <section id="book2" style="display: none;" class="hero2">
        <div class="container">
            <div class="left-col">
                <table>
                  <tr>
                    <th>Description</th>
                    <th>Date</th>
                    <th>Delete</th>
                  </tr>
                  <tr v-for="n in lim" :key= "n">
                    <td>{{BookingsArr[n-1]}}</td>
                    <td>{{BookingDates[n-1]}}</td>
                   <td><img @click="deleterecord(n-1)" height="40%" width="40%" src="../assets/icons8-trash-100.png" ></td
                  </tr>
                </table>
            </div>
        </div>
    </section> -->
    <div class="feet">
    <h5 style="text-align:center">Copyright © 2024 All Rights Reserved. Designed by <a href="kabelomakganye.co.za">Kabelo</a> </h5>
    </div>
  </div>
</template>

<script>
import acc from '../components/account.vue'
import swal from 'sweetalert'
export default {
  components: { 'acc-nt': acc },
  props: ['username', 'usersurname'],
  name: 'login',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      file: '1111',
      sugname: '',
      sugemail: '',
      sugmessage: '',
      resultsFetched_3: '',
      resultsFetched_4: '',
      resultsFetched_5: '',
      packagecount: 0,
      resultsFetched_6: '',
      timeslotscount: 0,
      slots: [],
      selectedtime: '',
      visitors: 1,
      chosenplannumber: 0,
      atload: 0,
      nextpage: '',

      signcarid: [],
      signname: '',
      signsurname: '',
      signemail: '',
      signplate: '',
      signcarname: [],
      totatwashcount: 0,
      washcount: 0,
      points: 0,
      lim: 4,
      date_: '',
      selectedcar: '',
      linkdata: 'https://kabelodatabase-4e42dc7fda46.herokuapp.com/' // 'http://localhost:3000/'
    }
  },

  unmounted () {
    window.removeEventListener('resize', this.removemenu)
  },
  methods: {
    directto (n) {
      window.location.href = `https://brajoecarwash.co.za/#/${n}` // 'http://localhost:8080/#/user'
    },
    shownumberofpeople () { // show option to add number of people
      console.log(this.selectedcar)
      for (let x = 0; x < this.resultsFetched_5.length; x++) {
        if (this.resultsFetched_5[x].packagename_ === this.selectedcar && this.resultsFetched_5[x].numberofpeople_ === 1) {
          document.getElementById('enternumberofpeople').style.display = 'inline'
          console.log(this.resultsFetched_5[x].numberofpeople_)
          this.chosenpackagenum = x
          break
        } else {
          document.getElementById('enternumberofpeople').style.display = 'none'
        }
      }
      this.visitors = 1
    },
    history (n) {
      swal('Loading', '', 'success', {
        buttons: false,
        timer: 1000
      })
      this.removemenu()
      // this.loadhistory()
      if (n === 1) {
        document.getElementById('book2').style.display = 'none'
        document.getElementById('book').style.display = 'inline'
        document.getElementById('infodata').style.display = 'none'
        document.getElementById('homebooking').style.display = 'inline'
      } else {
        document.getElementById('book2').style.display = 'inline'
        document.getElementById('book').style.display = 'none'
        document.getElementById('infodata').style.display = 'inline'
        document.getElementById('homebooking').style.display = 'none'
      }
    },
    async addbooking () {
      for (let x = 0; x < this.resultsFetched_5.length; x++) {
        if (this.resultsFetched_5[x].packagename_ === this.selectedcar) {
          this.chosenplannumber = x
          break
        }
      }
      if (this.visitors <= 0) {
        this.visitors = 1
      }
      document.getElementById('sendesugg').disabled = true
      document.getElementById('sendesugg').style.backgroundColor = '#F0998B'
      let allAreFilled = true /* check if all required fields are entered */
      document.getElementById('suggestions').querySelectorAll('[required]').forEach(function (i) {
        if (!allAreFilled) return
        if (!i.value) allAreFilled = false
      })
      if (allAreFilled) {
        const axios = require('axios')
        await axios.post(`${this.linkdata}fn_add_new_booking`, {
          email: this.signemail,
          usid: this.usid,
          pcid: this.resultsFetched_5[this.chosenplannumber].pcid_,
          numberofpeople: this.visitors,
          bookdate: this.date_,
          price: (this.visitors * this.resultsFetched_5[this.chosenplannumber].price_),
          selectedtime: this.selectedtime
        })
          .then((response) => {
            console.log(response)
            // alert(response.data)
            if (response.data === 'Invalid email') {
              swal('Invalid email', '', 'error')
            } else if (response.data === 'Something went wrong. please try again.') {
              swal('Something went wrong', '', 'error')
            } else if (response.data === 'Booking already exist please choose different slot') {
              swal('Booking already exist please choose different slot', '', 'error')
            } else {
              swal('Booking Made, copy sent to your email', '', 'success')
              this.selectedcar = ''
              this.visitors = 1
            }
          }, (error) => {
            console.log(error)
          })
      } else {
        // alert('fill up everything')
        swal('fill up everything', '', 'error')
      }
      document.getElementById('sendesugg').disabled = false
      document.getElementById('sendesugg').style.backgroundColor = '#31F300'
    },
    async addwash () {
      document.getElementById('sendesugg').disabled = true
      document.getElementById('sendesugg').style.backgroundColor = '#F0998B'
      /* if (this.selectedcar.length > 0) {
        for (let index = 0; index < this.lim; index++) {
          if (this.selectedcar === this.signcarname[index]) {
            let allAreFilled = true
            document.getElementById('suggestions').querySelectorAll('[required]').forEach(function (i) {
              if (!allAreFilled) return
              if (!i.value) allAreFilled = false
            })
            if (allAreFilled) {
              await fetch(`${this.linkdata}fn_add_wash/${this.date_}/${this.signcarid[index]}`)
                .then(response => response.json())
                .then(results => (this.resultsFetched_5 = results))
              if (this.resultsFetched_5[0].fn_add_wash === 0) {
                swal('Booking already added', '', 'warning', {
                  buttons: false,
                  timer: 1000
                })
              } else {
                swal('Saved', '', 'success', {
                  buttons: false,
                  timer: 1000
                })
              }
            } else {
              swal('Select date', '', 'error', {
                buttons: false,
                timer: 1000
              })
            }
          }
        }
      } else {
        swal('Select a Plan', '', 'error', {
          buttons: false,
          timer: 1000
        })
      } */
      /* Temporary message as we still developing */
      for (let x = 0; x < this.resultsFetched_5.length; x++) {
        if (this.resultsFetched_5[x].packagename_ === this.selectedcar) {
          this.chosenplannumber = x
          break
        }
      }
      if (this.visitors <= 0) {
        this.visitors = 1
      }
      swal('Booking coming soon Total R' + (this.visitors * this.resultsFetched_5[this.chosenplannumber].price_) + ' Deposit R' +
      ((this.visitors * this.resultsFetched_5[this.chosenplannumber].price_) / 2)
        , '', 'success', {
        buttons: false,
        timer: 5000
      })

      document.getElementById('sendesugg').disabled = false
      document.getElementById('sendesugg').style.backgroundColor = '#31F300'
    },
    direct () {
      swal('Image upload coming soon', '', 'success', {
        buttons: false,
        timer: 3000
      })
      // window.location.href = `${this.linkdata}jdndgskdjfhjhsdfbisfdhifhsdfhsdjsdjfhsjhdfkshdjksdhfhsdflsefsdklfjiieislx/${this.signname}`
    },
    checksession () {
      if (this.getCookie('userbrajoe') === 'none') {
        swal('', 'Session expired, login again', 'error', {
          buttons: false,
          timer: 3000
        })
        window.location.replace('https://www.diamondtreats.co.za/#/login')
        // window.location.replace('http://localhost:8080/#/login')
      } else {
        const d = new Date()
        d.setTime(d.getTime() + (1 * 1 * 1 * 1 * 180000)) // session will expire after a minute
        // d.setUTCHours(0, 0, 0)
        let expires = 'expires=' + d.toUTCString()
        document.cookie = 'usermissdiamonds' + '=' + this.signname + ';' + expires + ';path=/'
        document.cookie = 'surnamemissdiamonds' + '=' + this.signsurname + ';' + expires + ';path=/'
        document.cookie = 'emailmissdiamonds' + '=' + this.signemail + ';' + expires + ';path=/'
      }
    },
    logout () {
      const d = new Date()
      d.setTime(d.getTime() - (1 * 1 * 1 * 1 * 180000)) // session will expire after a minute
      // d.setUTCHours(0, 0, 0)
      let expires = 'expires=' + d.toUTCString()
      document.cookie = 'usermissdiamonds' + '=' + this.signname + ';' + expires + ';path=/'
      document.cookie = 'surnamemissdiamonds' + '=' + this.signsurname + ';' + expires + ';path=/'
      document.cookie = 'emailmissdiamonds' + '=' + this.signemail + ';' + expires + ';path=/'
      // add procedure that add to log when one login
      // }
      // window.location.replace('http://localhost:8080/#/login')
      window.location.replace('https://www.diamondtreats.co.za/#/login')
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
    toaccount () {
      this.checksession() // if cookies expired it logout
      // window.location.href = 'http://localhost:8080/#/account'
      window.location.replace('https://brajoecarwash.co.za/#/account')
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
    },
    async login () {
      await fetch(`${this.linkdata}get_user_miss/${this.signemail}`)
        .then(response => response.json())
        .then(results => (this.resultsFetched_3 = results))
      this.lim = this.resultsFetched_3.length
      this.signname = this.resultsFetched_3[0].name_
      this.signsurname = this.resultsFetched_3[0].surname_
      this.signplate = this.resultsFetched_3[0].platenum_
      this.usid = this.resultsFetched_3[0].usid_
      /* for (let index = 0; index < this.lim; index++) {
        this.signcarname[index] = this.resultsFetched_3[index].carname_
        this.signcarid[index] = this.resultsFetched_3[index].ucid_
      } */
      this.totatwashcount = this.resultsFetched_3[0].totatwashcount_
      this.washcount = this.resultsFetched_3[0].washcount_
      this.points = this.resultsFetched_3[0].points_
      console.log(this.resultsFetched_3)
      console.log(this.resultsFetched_3[0].points_)
      var d = new Date()
      var dmax = new Date()
      d.setTime(d.getTime() - (7 * 24 * 60 * 60 * 1000))
      dmax.setTime(dmax.getTime())
      /* var month = d.getMonth() + 1
      var year = d.getFullYear()
      var day = d.getDate() */

      var maxmonth = dmax.getMonth() + 1
      var maxyear = dmax.getFullYear()
      var maxday = dmax.getDate()
      /* if (month < 10) {
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
      } */
      // get list of packages
      await fetch(`${this.linkdata}get_all_packages`)
        .then(response => response.json())
        .then(results => (this.resultsFetched_5 = results))

      this.packagecount = this.resultsFetched_5.length
      for (let x = 0; x < this.resultsFetched_5.length; x++) {
        this.signcarname[x] = this.resultsFetched_5[x].packagename_
      }

      // get list of timeslots
      await fetch(`${this.linkdata}get_all_timeslots`)
        .then(response => response.json())
        .then(results => (this.resultsFetched_6 = results))

      this.timeslotscount = this.resultsFetched_6.length
      for (let x = 0; x < this.resultsFetched_6.length; x++) {
        this.slots[x] = this.resultsFetched_6[x].timefrom_
      }
      if (maxmonth < 10) {
        if (maxday < 10) {
          document.getElementById('myDate').min = maxyear + '-0' + maxmonth + '-0' + maxday
        } else {
          document.getElementById('myDate').min = maxyear + '-0' + maxmonth + '-' + maxday
        }
      } else {
        if (maxday < 10) {
          document.getElementById('myDate').min = maxyear + '-' + maxmonth + '-0' + maxday
        } else {
          document.getElementById('myDate').min = maxyear + '-' + maxmonth + '-' + maxday
        }
      }
    }
  },
  mounted () {
    window.addEventListener('resize', this.removemenu)
    if (this.getCookie('usermissdiamonds') === 'none') {
      // alert('Session expired, login again')
      swal('', 'Session expired, login again', 'error', {
        buttons: false,
        timer: 3000
      })
      // window.location.replace('http://localhost:8080/#/login')
      window.location.replace('https://www.diamondtreats.co.za/#/login') // 'http://localhost:8080/#/login'
    } else {
      this.signname = this.getCookie('usermissdiamonds')
      this.signsurname = this.getCookie('surnamemissdiamonds')
      this.signemail = this.getCookie('emailmissdiamonds')
      this.login()
    }
    // alert('welcome')
    // create a cookie that will help us coont number of page visits.
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
