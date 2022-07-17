<template>
  <h1>Join our Team of Writers</h1>
  <h3>
    On dasdas, writers earn a living doing what they love.<br />
    Getting started is easy. Just pay a one time <span style="font-weight:700">$25</span> 
    fee and everything is ready to go.
  </h3>
  <div id="btn-contain" >
    <button id="btn-contain__btn" @click="makePayment()" >JOIN US</button>
  </div>
</template>

<!-- <script type="application/javascript" src="https://checkout.flutterwave.com/v3.js"></script> -->
<script>

export default {
  name: 'JoinUs',
  methods: {
    makePayment() {
      window.FlutterwaveCheckout({
        public_key: "FLWPUBK_TEST-SANDBOXDEMOKEY-X",
        tx_ref: "titanic-48981487343MDI0NzMx",
        amount: 54600,
        currency: "NGN",
        payment_options: "card",
        callback: function () {
          setTimeout(function() {
            window.location.href = process.env.BASE_URL;
          }, 10000);
        },
        meta: {
          consumer_id: 23,
          consumer_mac: "92a3-912ba-1192a",
        },
        customer: {
          email: "rose@unsinkableship.com",
          phone_number: "08102909304",
          name: "Rose DeWitt Bukater",
        },
        customizations: {
          title: "The Titanic Store",
          description: "Payment for an awesome cruise",
          logo: "https://www.logolynx.com/images/logolynx/22/2239ca38f5505fbfce7e55bbc0604386.jpeg",
        },
      });
    },
  },
  mounted() {
    let Script = document.createElement("script");
    Script.setAttribute("src","https://checkout.flutterwave.com/v3.js")
    document.head.appendChild(Script);
  }
}
</script>
<style lang="scss" scoped>
h1 {
  font-weight: 500;
  text-align: center;
  margin-bottom: 12px;
  color: #2C2C2C;
}

h3 {
  font-size: 22px;
  font-weight: 500;
  color: #6E6E6E;
  text-align: center;
  line-height: 32px;
  margin-bottom: 35px;
}

#btn-contain {
  width: 100%;
  display: flex;
  justify-content: center;

  &__btn {
    width: 177px;
    height: 45px;
    background-color: #000;
    color: #FFF;
    font-size: 18px;
    font-weight: 500;
    cursor: pointer;
  }
}
</style>