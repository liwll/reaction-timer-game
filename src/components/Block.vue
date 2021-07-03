<template>
  <div :class="blockClass" @click="stopTimer">
      <div v-if="timer === null">Click When The Box Turns Green</div>
      <div v-else>Click!</div>
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            blockClass: "play-area",
            timer: null,
            reactionTime: 0,
        }
    },
    mounted() {
        setTimeout(() => {
            this.blockClass = "block";
            this.startTimer();
        }, this.delay);
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
               this.reactionTime += 5; 
            }, 5);
        },
        stopTimer() {
            clearInterval(this.timer);
            this.$emit('stop', this.reactionTime);
        } 
    },
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
.play-area {
    width: 400px;
    border-radius: 20px;
    background: #af0f0f;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>