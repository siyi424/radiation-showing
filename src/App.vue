<template>
  <div id="app">
    <div class="header">
      <h1 class="title-center">监测数据显示屏</h1>
    </div>

    <!-- 中间body部分 -->
    <div class="body">
      <div id="wheather"><div-weather :weather="DataWeather"></div-weather></div>
      <div id="chart"><chart-radi :datalist="DataList"></chart-radi></div>
      <div id="dataset"><data-radi :dataset="DataList"></data-radi></div>
      <!-- <button @click="plus1">Plus Data</button> -->
    </div>


    <!-- 结尾展示小组成员 -->
    <div class="footer">
      <div>
        小组成员：韩立荟、胡伟、黄思怡 
      </div>
      <div>
        科研训练题目：智能化个人辐射剂量率检测系统研究
      </div>

      <div id="footer-right">
        <img src="./assets/logo.png">
      </div>

    </div>
    
  </div>
</template>



<script>
import ChartRadi from './components/ChartRadi.vue'
import DataRadi from './components/DataRadi.vue'
import DivWeather from './components/DivWeather.vue'
import axios from 'axios'



export default {
  components: { ChartRadi, DataRadi, DivWeather},
  name: 'app',
  data: () => ({
    DataList: [],
    DataWeather: [],
  }),
  async created() {
    // const res = await axios.get("/DataList.json");
    await axios.get('DataList.json').then((res) => {
      this.DataList = res.data
    }),

    await axios.get('DataWeather.json').then((res) => {
      this.DataWeather = res.data
    })
  },
  
  // methods: {
  //   plus1() {
  //     let temp = {"time": "2022/11/02",
  //       "value": 115,
  //       "isSafed": "安全"};
  //     this.DataList.push(temp)
  //   }
  // }
}
</script>




<style>
* {
  font-family: Microsoft YaHei;
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

#app {
  background: #073A4B;
  color: whitesmoke;
}

/* animate */
@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translate3d(0, -100%, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}


@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translate3d(-100%, 0, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}


@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translate3d(100%, 0, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translate3d(0, 100%, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}



/* header */
.header {
  height: 8vh;
  animation-name: fadeInDown;
  animation-duration: 2s;
  display: flex;
  align-items: center;
  justify-content: center;
  background: gray;
  box-shadow: black 0 2px 40px ;
}

.title-center {
  text-align: center;
  color:whitesmoke;
}


/* body */
.body {
  display: flex;
  flex-direction: column;
  align-items: stretch;
  padding: 30px;

  width: 60%;
  margin: 0 auto;
}

#chart {
  background: rgba(225,225,225,0.9);
  animation-name: fadeInLeft;
  animation-duration: 2s;
  flex: 1;
  box-shadow: black 2px 2px 40px;
}

#dataset {
  flex: 2;
  animation-name: fadeInRight;
  animation-duration: 2s;
  margin: 60px 0;
  box-shadow: black 2px 2px 40px;
}


/* footer */
.footer {
  display: flex;
  max-height: 14.4%;
  justify-content: space-between;
  align-items: center;
  animation-name: fadeInUp;
  animation-duration: 2s;
  padding: 0 40px;

  background: gray;
  box-shadow: black 0px 2px 40px;

}

#footer-right img{
  align-items: stretch;
}
</style>