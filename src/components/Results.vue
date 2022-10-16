<template>
  <div class="reaction">
    <p>Reaction Time: {{this.score}}ms</p>
</div>
<p>Rank: {{this.rank}}</p>
</template>

<script>
export default {
    props: ["score"],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if (this.score >= 180 && this.score < 250){
            this.rank = "Gamer"
        } else if (this.score >= 250 && this.score < 450){
            this.rank = "Casual"
        } else if (this.score >= 450){
            this.rank = "Old Man"
        }else{
            this.rank = "Pro Player"
        }
    }
}
</script>

<style>
    .reaction{
        width: 300px;
        padding: 2px 0px;
        margin: 10px auto;
        text-align: center;
        color: white;
        border: 2px solid black;
        border-radius: 10px;
        background: rgba(0,0,0,.45);
    }
</style>