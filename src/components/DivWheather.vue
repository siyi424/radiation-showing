<template>
    <div class="allInfo">
        <div id="temperature">{{this.temp}}</div>
        <div id="location">{{this.loc}}</div>
        <div id="humidity">{{this.humi}}</div>
    </div>
</template>

<script>
import DataWheather from '../../public/DataWheather.json'

export default {
    data() {
        let temp = DataWheather[0].temperature;
        let loc = DataWheather[0].location;
        let humi = DataWheather[0].humidity;

        return {
            temp,
            loc,
            humi
        }
    },

}
</script>

<style scoped>
.allInfo {
    display: felx;
    flex-direction: row;
    height: 500px;
}

#temperture {
    flex: 1;
}

#location {
    flex: 1;
}

#humidity {
    flex: 1;
}
</style>