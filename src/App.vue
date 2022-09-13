<template>
  <div id="app">
    <div class="header">
      <h1 class="title-center">监测数据显示屏</h1>
    </div>

    <!-- 中间body部分 -->
    <div class="body">
      <div id="wheather"><div-wheather></div-wheather></div>
      <div id="chart"><chart-radi v-if='DataList.length' :datalist="DataList"></chart-radi></div>
      <div id="dataset"><data-radi :dataset="DataList"></data-radi></div>
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
import DivWheather from './components/DivWheather.vue'
// 引入数据
import DataList from '../public/DataList.json'


export default {
  components: { ChartRadi, DataRadi, DivWheather},
  name: 'app',
  data() {
    return {
      DataList
    }
  }
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
  background-image: radial-gradient( circle farthest-corner at 10% 20%,  rgba(90,92,106,1) 0%, rgba(32,45,58,1) 81.3% );
  display: flex;
  flex-direction: column;
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
  flex: 1;
  animation-name: fadeInDown;
  animation-duration: 2s;
  display: flex;
  align-items: center;
  justify-content: center;
}

.title-center {
  text-align: center;
  color:whitesmoke;
}


/* body */
.body {
  flex: 11;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  padding: 20px 40px;
}

#chart {
  background: rgba(225,225,225,0.9);
  flex: 1;
  animation-name: fadeInLeft;
  animation-duration: 2s;
  margin-right: 20px;
}

#dataset {
  flex: 1;
  animation-name: fadeInRight;
  animation-duration: 2s;
  margin-left: 20px;
}


/* footer */
.footer {
  flex: 2;
  display: flex;
  max-height: 14.4%;
  justify-content: space-between;
  align-items: center;
  animation-name: fadeInUp;
  animation-duration: 2s;
  padding: 0 40px;

}

#footer-right img{
  align-items: stretch;
}
</style>