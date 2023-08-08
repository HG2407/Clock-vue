<template>
    <div class="clock">
          <li style="--i:1">1</li>
          <li style="--i:2">2</li>
          <li style="--i:3">3</li>
          <li style="--i:4">4</li>
          <li style="--i:5">5</li>
          <li style="--i:6">6</li>
          <li style="--i:7">7</li>
          <li style="--i:8">8</li>
          <li style="--i:9">9</li>
          <li style="--i:10">10</li>
          <li style="--i:11">11</li>
          <li style="--i:12">12</li>


          <div class="hand hr" style="--wid:0.5rem; --hght:5rem; --clr:rgb(238, 192, 244);" v-bind:style="{transform: hourRotate}"></div>
          <div class="hand min" style="--wid:0.4rem; --hght:8rem; --clr:rgb(247, 84, 247);"  v-bind:style="{transform: minRotate}"></div>
          <div class="hand sec" style="--wid:0.2rem; --hght:12rem; --clr:rgb(248, 155, 170);" v-bind:style="{transform: secRotate}"></div>
          
    </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'clock',

  mounted() {

    this.intervals();

  },

  data() {
    return {
      hourRotate: "rotateZ(0deg)",
      minRotate: "rotateZ(0deg)",
      secRotate: "rotateZ(0deg)" 
    }
  },
  
  methods: {
    intervals() {
        setInterval(this.updateClock, 1000);
    },

    updateClock() {
      let now = new Date();
      let seconds = now.getSeconds()/60*360;
      let minutes = now.getMinutes()/60 * 360;
      let hours = now.getHours()/12 *360;
       console.log(minutes, seconds, hours);
      this.secRotate = `rotateZ(${seconds}deg)` ;
      this.hourRotate = `rotateZ(${hours}deg)`;
      this.minRotate = `rotateZ(${minutes}deg)`;
      

    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  *, 
  *::before,
  *::after {
    box-sizing: border-box;
  }

  .clock {
    width: 30rem;
    height: 30rem;
    background-color:springgreen;
    border-radius: 50%;
    border: 1rem solid greenyellow;
    position: relative;
    text-align: center;
  }

  li {
    position: absolute;
    text-align: center;
    color: #fff;
    list-style: none;
    font-size: 2rem;
    font-weight: bold;
    width: 100%;
    height: 100%;
    transform: rotate(calc(30deg*var(--i)));
    font-family: 'Poppins', sans-serif;
  }

  .clock::after {
    content: '';
    width: 1rem;
    height: 1rem;
    background-color: white;
    border-radius: 50%;
    position: absolute;
    bottom: 50%;
    left: 49%;
  }
  
  .hand {
    position: absolute;
    width:var(--wid);
    height: var(--hght);
    background-color: var(--clr);
    bottom: 51%;
    left: 50%;
    /* transform: rotateZ(60deg); */
    transform-origin: bottom;
  }

  /* .sec {
    /* transition-property: transform;
    transform-origin:bottom; */
    /* bottom: 45%;
  } */ 

</style>
