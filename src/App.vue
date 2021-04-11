<template>
  <div id="app">
    <gen-inv v-if="page=='GenInv'" @addinvoice="addinvoice" @changepage="changepage"/>
    <home v-if="page=='home'" @changepage="changepage" />
    <view-inv :invoices="invoices" v-if="page=='ViewInv'" @changepage="changepage"/>
  </div>
</template>

<script>
import GenInv from "@/components/GenInv.vue"
import Home from "@/components/Home.vue"
import ViewInv from "@/components/ViewInv.vue"
export default {
  name: 'App',
  components : { 
    Home, ViewInv, GenInv
  },
  data() {
    return {
      page: "home",
      invoices: [
        {
          inum: 145,
          idate: "12-04-2021",
          ddate: "27-04-2021",
          cname: "Slitherine Studios",
          addr: "195 Ber Street, NORWICH, NR1 3HB",
          cnum: "9876543210",
          eid: "abc@xyz.com",
          pmet: "Pay Using Cash",
          items: [
            {
              sn: 1,
              des: "Labour Cost",
              ucst: 5,
              qty: 60,
              amt: 300
            },
            {
              sn: 2,
              des: "Material",
              ucst: 25,
              qty: 100,
              amt: 2500
            }
          ],
          tot:2800
        }
       ]
    }
  },
  methods: {
    changepage(page){
      this.page=page;
    },
  addinvoice(invoice) {

    this.invoices.push(invoice)
  }
  }

}
</script>

<style>

</style>
