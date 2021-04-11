<template>
  <div>
    <div class="PageTitle" style="height: 40px; text-align: center;">        
            <h1>Studio Fever</h1>
        </div>
        <br>
        <div class="welcome" style="  text-align: center;">
            <h3>Welcome to the Studio Fever Invoicing Application</h3>    
        </div>        
        <div class="logo" style="  text-align: center;">
            <img src=https://i.ibb.co/NtYNfD2/Logo.jpg alt="Logo" width ="250px" height="200px"/>
        </div>
        <br>
        <div class="add" style="  text-align: center;"    >    
            <b>195 Ber Street</b><br>
            <b>NORWICH</b><br>
            <b>NR1 3HB</b><br>
         </div>
        <br><br>
        <div class="tasks" style="height: 40px;   padding-top: 20px; text-align: center;">
        <button @click="$emit('changepage', 'GenInv')">Generate New Invoice</button>
        <button @click="$emit('changepage', 'ViewInv')">View Invoices</button>
        </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
}
</script>

    <style>
        * {
            margin: 0px;
            padding: 0px;
        }

        .app{
            height: 500px;
            
        }
        body {
            background-color: #c1d3fe;
            color: #5885e7;
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