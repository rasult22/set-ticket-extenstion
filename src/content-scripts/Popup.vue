
<template>
 <div class="overlay" v-show="visible">
    <div class="popup">
      <h1>Legendary ... wait for it</h1>
      <pre>
        {{ cookie }}
      </pre>
      <button @click="getTicket">Get Ticket</button>
    </div> 
 </div>
</template>

<script>
export default  {
  name: 'Popup',
  data () {
    return {
      visible: false,
      cookie: 'ticket',
      sms: false
    }
  },
  methods: {
    getTicket () {
      const testURL = 'https://api.coinsave.us/user/login'
      const testBody = {
        email: "rasul.turganoff@gmail.com",
        password: "Liverpool"
      }
      const kaspiURL = 'https://test.kaspi.kz/signin/api/SignIn'
      const reqBody = {
        request: {
          login: "7774003640",
          password: "12345678",
          deviceId: "333",
          installationId: "insomnia7",
          clientAuthType: 0,
        }
      }

      if (this.sms) {
        reqBody.request.SMSCode = "9999"
      }
      // content type application/json

      fetch(testURL, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(testBody)
      }).then(response => response.json())
      .then(data => {
        this.cookie = data
      })
    },
  }
}
</script>

<style>
  .overlay {
    position: fixed;
    width: 200px;
    max-height: 200px;
    top: 0px;
    right: 0px;
    background-color: black;
    z-index: 50;
  }
  .popup {
    padding: 10px;
    top: 4px;
    position: absolute;
    right: 4px;
    background-color:white;
    border-radius: 8px;
    width: 100%;
  }

</style>