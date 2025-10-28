<script>
    export default {
        // Add code if/as necessary
        // Hint: Add properties subject, entry and mood
        props:{
            id:Number, 
            subject: String, 
            entry: String, 
            mood: String, 
        }, 
        computed:{
            imgLoc(){
                return `/assets/${this.mood.toLowerCase()}.png`
            }
        }, 


    }
</script>


<template>
    <!-- TODO: add your template code here. Use boostrap card --> 
<div class="card" style="width: 18rem;">
    <img :src="imgLoc" class="card-img-top" alt="bart simpsons">
    <div class="card-body">
    <b><p class="card-text">Blog {{ id}}</p></b>
    <p class="card-text">{{ entry }}</p>
  </div>
</div>
</template>

<style scoped>

p {
    text-align: left;
}


</style>
