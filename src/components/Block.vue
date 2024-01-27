<template>
  <div class="block" v-if="showBlock" @click="stopTime">Click Here</div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return {
            showBlock:false,
            score: 0,
            timer: null
        }
    },

    methods: {
        startTime() {
            this.timer = setInterval(()=>{
                this.score+=50;
            },50)
        },
        stopTime() {
            clearInterval(this.timer)
            this.$emit('endGame',this.score)
        }
    },

    mounted() {
        setTimeout(()=>{
            this.showBlock = true;
            this.startTime();
        },this.delay)
    },

}
</script>

<style>
    .block {
        background-color: cyan;
        width: 400px;
        height: 300px;
        margin: 40px auto;
        padding-top: 20px;
    }
</style>