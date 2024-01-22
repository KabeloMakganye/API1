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
                    <li class="current"><a href="https://brajoecarwash.co.za/#/">Home</a></li>
                    <!--<li><a @click="toaccount()">Account</a></li>-->

                </ul>

                <ul class="secondary-nav">
                  <!-- <input id="sendesuggs" type="button" @click="direct" class="send-message-cta" value="Upload Image"> -->
                    <li><a @click="direct" href="#">Upload Image</a></li>
                    <li><a @click="directto('user')">Main page</a></li>
                    <!-- <li><a href="#">Contact</a></li> -->
                    <!-- <li id="homebooking" ><a  @click="history(2)">History</a></li>
                    <li id="infodata" style="display: none;"><a  @click="history(1)">add wash</a></li> -->
                    <li class="go-premium-cta"><a @click="logout">Logout</a></li>
                </ul>
            </nav>
        </div>
    </div>
    <section class="heros">
        <div class="container">
            <div class="left-col">
                <table>
                  <tr>
                    <th>Date</th>
                    <th>Amount</th>
                  </tr>
                  <tr v-for="n in booksize" :key= "n">
                    <td>{{dates[n-1]}}</td>
                    <td>R{{amounts[n-1]}}</td>
                    <td><img @click="deleterecord(n-1)" height="40%" width="40%" src="../assets/icons8-trash-100.png" ></td>
                  </tr>
                  <tr v-if="booksize == 0" >
                    <td>no record</td>
                    <td></td>
                  </tr>
                  <tr>
                    <td>
                      <input  type= "date" id="myDate" v-model="bookdate_" min="2022-11-26" max="2022-11-26" required pattern="\d{4}-\d{2}-\d{2}"> <br>
                    </td>
                    <td>
                      <input type="number" v-model="bookamount_">
                    </td>
                  </tr>
                </table>
                <input id="sendesugg2" type="button" @click="newrecord"  value="Save Record" >
            </div>
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
    <h5 style="text-align:center">Copyright © 2023 All Rights Reserved. Designed by <a href="">car wash</a> </h5>
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
      booksize: '-5',
      dates: [],
      amounts: [],
      bookdate_: '',
      bookamount_: '',
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
      lim: 0,
      date_: '',
      selectedcar: '',
      linkdata: 'https://kabelodatabase-4e42dc7fda46.herokuapp.com/'
    }
  },

  unmounted () {
    window.removeEventListener('resize', this.removemenu)
  },
  methods: {
    async getbook () {
      await fetch(`${this.linkdata}get_book`)
        .then(response => response.json())
        .then(results => (this.resultsFetched_5 = results))
      this.booksize = this.resultsFetched_5.length
      for (let x = 0; x < this.resultsFetched_5.length; x++) {
        this.dates[x] = this.resultsFetched_5[x].date_
        this.amounts[x] = this.resultsFetched_5[x].amount_
      }
    },
    directto (n) {
      window.location.href = `https://brajoecarwash.co.za/#/${n}` // 'http://localhost:8080/#/user'
    },
    deleterecord (n) {
      swal('Delete Coming Soon', '', 'success', {
        buttons: false,
        timer: 3000
      })
    },
    async newrecord () {
      if (this.bookdate_.length > 0 && this.bookamount_.length > 0) {
        await fetch(`${this.linkdata}fn_add_book/${this.bookdate_}/${this.bookamount_}`)
          .then(response => response.json())
          .then(results => (this.resultsFetched_5 = results))
        if (this.resultsFetched_5[0].fn_add_book === 1) {
          swal('Date already added', '', 'warning', {
            buttons: false,
            timer: 1000
          })
        } else {
          swal('Saved', '', 'success', {
            buttons: false,
            timer: 1000
          })
        }
        this.getbook()
      }
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
    async addwash () {
      document.getElementById('sendesugg').disabled = true
      document.getElementById('sendesugg').style.backgroundColor = '#F0998B'
      if (this.selectedcar.length > 0) {
        for (let index = 0; index < this.lim; index++) {
          if (this.selectedcar === this.signcarname[index]) {
            let allAreFilled = true /* check if all required fields are entered */
            document.getElementById('suggestions').querySelectorAll('[required]').forEach(function (i) {
              if (!allAreFilled) return
              if (!i.value) allAreFilled = false
            })
            if (allAreFilled) {
              await fetch(`${this.linkdata}fn_add_wash/${this.date_}/${this.signcarid[index]}`)
                .then(response => response.json())
                .then(results => (this.resultsFetched_5 = results))
              if (this.resultsFetched_5[0].fn_add_wash === 0) {
                swal('wash already added', '', 'warning', {
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
        swal('Select a car', '', 'error', {
          buttons: false,
          timer: 1000
        })
      }
      document.getElementById('sendesugg').disabled = false
      document.getElementById('sendesugg').style.backgroundColor = '#31F300'
    },
    direct () {
      window.location.href = `${this.linkdata}jdndgskdjfhjhsdfbisfdhifhsdfhsdjsdjfhsjhdfkshdjksdhfhsdflsefsdklfjiieislx/${this.signname}`
    },
    checksession () {
      if (this.getCookie('userbrajoe') === 'none') {
        swal('', 'Session expired, login again', 'error', {
          buttons: false,
          timer: 3000
        })
        window.location.replace('https://brajoecarwash.co.za/#/login')
        // window.location.replace('http://localhost:8080/#/login')
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
      await fetch(`${this.linkdata}get_user/${this.signemail}`)
        .then(response => response.json())
        .then(results => (this.resultsFetched_3 = results))
      this.lim = this.resultsFetched_3.length
      this.signname = this.resultsFetched_3[0].name_
      this.signsurname = this.resultsFetched_3[0].surname_
      this.signplate = this.resultsFetched_3[0].platenum_
      for (let index = 0; index < this.lim; index++) {
        this.signcarname[index] = this.resultsFetched_3[index].carname_
        this.signcarid[index] = this.resultsFetched_3[index].ucid_
      }
      this.totatwashcount = this.resultsFetched_3[0].totatwashcount_
      this.washcount = this.resultsFetched_3[0].washcount_
      this.points = this.resultsFetched_3[0].points_
      console.log(this.resultsFetched_3)
      console.log(this.resultsFetched_3[0].points_)
      var d = new Date()
      var dmax = new Date()
      d.setTime(d.getTime() - (7 * 24 * 60 * 60 * 1000))
      dmax.setTime(dmax.getTime())
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
  mounted () {
    window.addEventListener('resize', this.removemenu)
    if (this.getCookie('userbrajoe') === 'none') {
      // alert('Session expired, login again')
      swal('', 'Session expired, login again', 'error', {
        buttons: false,
        timer: 3000
      })
      // window.location.replace('http://localhost:8080/#/login')
      window.location.replace('https://brajoecarwash.co.za/#/login') // 'http://localhost:8080/#/login'
    } else {
      this.signname = this.getCookie('userbrajoe')
      this.signsurname = this.getCookie('surnamebrajoe')
      this.signemail = this.getCookie('emailbrajoe')
      this.login()
      this.getbook()
    }
    // alert('welcome')
    // create a cookie that will help us coont number of page visits.
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
