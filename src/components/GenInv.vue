<template>
  <div>
    <div class="body">
            <div class="top">
                <table class="topdiv">
                    <tr>
                        <td>
                            <img src=https://i.ibb.co/NtYNfD2/Logo.jpg alt="Logo" width ="125px" height="100px"/>
                        </td>
                        <td>
                            Invoice Number : <input type="number" v-model="invoice.inum">
                            <br>
                            Invoice Date : <input type="date" v-model="invoice.idate">
                            <br>
                            Due Date : <input type="date" v-model="invoice.ddate">
                        </td>
                    </tr>
                </table>
            </div>
            <div class="custdetail">
                <table class="secdiv">
                    <tr>
                        <td>
                            <b>195 Ber Street</b><br>
                            <b>NORWICH</b><br>
                            <b>NR1 3HB</b><br>
                        </td>
                        <td>
                            To : <input type="text" placeholder="Customer Name" v-model="invoice.cname">
                            <br>
                            Address : <textarea placeholder="Address" v-model="invoice.addr"></textarea>
                            <br>
                            Number : <input type="number" placeholder="Contact Number" v-model="invoice.cnum">
                            <br>
                            E-mail : <input type="url" placeholder="E-mail id" v-model="invoice.eid">
                        </td>
                    </tr>
                </table>
            </div>
            <div class="paymet" style="text-align: center;">
                <h3>
                    Payment Method
                </h3>
                <table>
                    <tr>
                        <p>Please Select Payment Method:</p>
                        <input type=text v-model="invoice.pmet">
                    </tr>
                </table>
            </div>
            <div class="details">
                <table>
                    <tr>
                    <th>Description</th>
                    <th>Unit Cost</th>
                    <th>Quantity</th>
                    <th>Amount</th>
                    </tr>
                    <tr v-for="(item, i) in invoice.items" :key="i">
                        <td><input type="text" v-model="item.des"></td>
                        <td>$ <input type="number" v-model="item.ucst"></td>
                        <td><input type="number" v-model="item.qty"></td>
                        <td>{{item.ucst*item.qty}}</td>
                    </tr>
                    <tr><td><button @click="addrow">Add Row</button></td></tr>
                    <tr>
                        <td colspan="3"></td>
                        <td>Total : $ {{Total}}</td>
                    </tr>
                </table>
            </div>
            <div class="lastdiv" style="text-align: center;">
                <button @click="$emit('changepage', 'home')">Home Page</button>
                <button @click="submit">Submit</button>
            </div>
        </div>
  </div>
</template>

<script>
export default {
  name: 'GenInv',
  computed: {
    Total() {
      return this.invoice.items.reduce(
        (acc, item) => acc + item.ucst * item.qty,
        0
      );
    },
  },
  methods:{
      addrow(){
          this.invoice.items.push({des: "", ucst:0, qty:1 })
        },
        submit(){
            this.invoice.tot=this.total
            this.$emit("addinvoice", this.invoice)
            this.$emit("changepage", "ViewInv")
        },

  },
  data(){
      return{
        invoice:{
          inum: null,
          idate: "",
          ddate: "",
          cname: "",
          addr: "",
          cnum: "",
          eid: "",
          pmet: "",
          items: [
            {
              des: "",
              ucst: null,
              qty: null
            }
          ],
          tot:2800
        }
      }
  }
}

</script>

<style>
    body{
            color: white;
            margin: 0;
        }
        button{
            background: #abc4ff;
            padding: 5px 10px;
            border: 1px solid #abc4ff;
            color: white;
            border-radius: 5px;
        }
        input{
            margin: 5px;
            padding: 5px 10px;
            color: #8d7f7f;
            background: transparent;
            outline: none;
            border: 1px solid #8d7f7f;
            border-radius: 5px;
        }
        .body{
            display: flex;
            flex-direction: column;
        }
        .topdiv{
            width: 50vw;
            display: flex;
        }
        
        .topdiv tr {
            width: 50vw;
            display: flex;
            justify-content: space-between;
        }
        .custdetail tr {
            width: 50vw;
            display: flex;
            justify-content: space-between;
        }
        .topdiv td {
             display: flex;
             flex-direction: column;
        }
        .topdiv td div {
             display: flex;
             flex-direction: column;
        }
        .custdetail td {
             display: flex;
             flex-direction: column;
        }
        .custdetail td div {
             display: flex;
             flex-direction: column;
        }
        img{
            margin: 50px;
        }
</style>