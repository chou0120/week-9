<template>
  <div>
     <h1>{{ msg }}</h1>
    <div class="box">
        <img class="img1" :src="img">
        <div class="para1">
        <p>{{ paragraph }}</p>
       </div>
    </div>
    <div class="box">
       <div class="para2">
        <p>{{ paragraph }}</p>
       </div>
       <img class="img2" :src="img">
    </div>
  </div>
</template>

<script>
export default {
    name: "homes",
    data() {
return  {
        img:'https://placekitten.com/300/300',
        msg: 'Welcome to My About Page',
        paragraph: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Accusamus numquam debitis dolorem expedita ad animi modi necessitatibus sequi fugit, neque fugiat sunt doloremque rerum minus, praesentium atque adipisci aspernatur officiis?',

    }
}
 }
</script>
<style>
.box{
    width:80%;
    margin:0 auto;
    display: flex;
    margin-bottom: 2rem;
    
}
.img1 {
 float:left;
 margin-right: 2rem;
}
.img2 {
 float: right;
 margin-left: 2rem;
}
.para1{
    float:right;
    text-align: left;
}
.para2{
    float:left;
    text-align: right;
}
</style>
