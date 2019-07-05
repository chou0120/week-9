<template>
    <div class="footer">
    <p>Copyright by &copy; {{ AuthorName }} - 20{{ Year }}-20{{ Year + 5 }}</p>  
    </div>
</template>
<script>
export default {
    data(){
        return{
            AuthorName: 'Samuel Choudhary',
            Year: 19
        }
    }
}
</script>
<style>
.footer{
    background-color: beige;
    padding: 1rem;
}
</style>
