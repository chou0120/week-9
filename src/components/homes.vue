<template>
    <div>
     <h1>{{ msg }}</h1>
    <div class="box">
        <img class="img" :src="img">
        <div class="para">
       
        <p>{{ paragraph }}</p>
        <p>{{ paragraph }}</p>
       </div>
    </div>
    </div>
</template>

<script>
export default {
    name: "homes",
    data() {
return  {
        img:'https://placekitten.com/300/300',
        msg: 'Welcome to My App',
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
    
}
.img {
 float:left;
 margin-right: 2rem;
}
.para{
    float:right;
    text-align: left;
}
</style>
