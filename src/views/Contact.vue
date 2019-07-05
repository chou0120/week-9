<template>
    <div >
        <h1>Contact</h1>
       <div class="contact">
           <div>
               <h2>Address</h2>
               <p>{{  Address }}</p>
               <p>{{  Phone}}</p>
           </div>

            <div>
                <h2>Working Hours</h2>
            <ul>
                <li v-for="day in days">
            {{ day  }}
            </li>
        </ul>
        </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return{
            Address: '1345 Woodroffe Aveune, Ottawa, ON',
            Phone: '613- 000-000',
            days: [
                "Monday: 08:00-05:00","Tuesday: 08:00-05:00","Wednesday: 08:00-05:00",
                "Thursday: 08:00-05:00","Friday: 08:00-05:00","Saturday: 08:00-05:00",
                "Sunday: 08:00-05:00",
                
               

            ]
        }
    }
}
</script>
<style>
.contact{
    display:flex;
}
.contact div{
    width:20%;
    padding:2rem;
    text-align:left;
    margin:0 auto;
    }
ul{
    list-style: none;
}

</style>
