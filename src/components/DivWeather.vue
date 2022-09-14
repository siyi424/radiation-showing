<template>
    <div class="allInfo">
        <div id="location">{{this.loc}}</div>
        <div id="info">温度：{{this.temp}} , 湿度：{{this.humi}}</div>
    </div>
</template>

<script>
import DataWeather from '../../public/DataWeather.json'

export default {
    data() {
        let temp = DataWeather[0].temperature;
        let loc = DataWeather[0].location;
        let humi = DataWeather[0].humidity;

        return {
            temp,
            loc,
            humi
        }
    },

}
</script>

<style scoped>
@keyframes bounceInLeft {
  from,
  60%,
  75%,
  90%,
  to {
    animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  0% {
    opacity: 0;
    transform: translate3d(-3000px, 0, 0) scaleX(3);
  }

  60% {
    opacity: 1;
    transform: translate3d(25px, 0, 0) scaleX(1);
  }

  75% {
    transform: translate3d(-10px, 0, 0) scaleX(0.98);
  }

  90% {
    transform: translate3d(5px, 0, 0) scaleX(0.995);
  }

  to {
    transform: translate3d(0, 0, 0);
  }
}

@keyframes bounceInRight {
  from,
  60%,
  75%,
  90%,
  to {
    animation-timing-function: cubic-bezier(0.215, 0.61, 0.355, 1);
  }

  from {
    opacity: 0;
    transform: translate3d(3000px, 0, 0) scaleX(3);
  }

  60% {
    opacity: 1;
    transform: translate3d(-25px, 0, 0) scaleX(1);
  }

  75% {
    transform: translate3d(10px, 0, 0) scaleX(0.98);
  }

  90% {
    transform: translate3d(-5px, 0, 0) scaleX(0.995);
  }

  to {
    transform: translate3d(0, 0, 0);
  }
}

  

.allInfo {
    text-align: center;
    height: 100vh;
    margin-top: -10%;
    color: black;
    background: url("../assets/border.png") center/contain no-repeat ;

    animation-name: bounceInLeft;
    animation-duration: 2s;
}

#location {
    padding-top: 35%;
    font-size: 120px;

    animation-name: bounceInRight;
    animation-duration: 2s;
}

#info {
    font-size: 30px;
    animation-name: bounceInRight;
    animation-duration: 2s;
}

</style>