<template>
  <div>
    <div class="List" style="text-align: center;">
            <h1>Invoices</h1>
            <table style="width: 90%;">
                <tr>
                    <th>Sr. No.</th>
                    <th>Date</th>
                    <th>Invoice No.</th>
                    <th>Client Name</th>
                    <th>Total Amount</th>
                    <th>View</th>
                    <th>Print</th>
                    <th>Mail Invoice</th>
                </tr>
                <tr v-for="invoice in invoices" :key=invoice.inum>
                    <td>{{invoice.inum}}</td>
                    <td>{{invoice.idate}}</td>
                    <td>{{invoice.inum}}</td>
                    <td>{{invoice.cname}}</td>
                    <td>${{invoice.tot}}</td>
                    <td>
                        <button>View</button>
                    </td>
                    <td>
                        <button>Print</button>
                    </td>
                    <td>
                        <button>Mail Invoice</button>
                    </td>
                </tr>
            </table>
            <br>
            <button @click="$emit('changepage', 'home')">Home Page</button>    
        </div>
  </div>
</template>

<script>

export default {
  name: 'ViewInv',
    props: [
        "invoices"
    ]
}
</script>

<style>
        * {
            margin: 0px;
            padding: 0px;
        }
        table, th, td {
            border: 1px solid black;
            border-collapse: collapse;
        }
        button{
        
            background-color: #5885e7;
            border: 1px solid #5885e7;
            border-radius: 5px;
            padding: 10px;
            color: white;
            margin: 5px;
        }
</style>