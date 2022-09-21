<template>
    <div class="allInfo">
        <div id="location">{{weather[0].location}}</div>
        <div id="info">温度：{{weather[0].temperature}} , 湿度：{{weather[0].humidity}}</div>
    </div>
</template>

<script>

export default {
    props: ['weather'],
    

    watch: {
      weather: {
        deep: true,
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