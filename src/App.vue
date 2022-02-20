<template>
	<Speedometer :speed="speed" :maxSpeed="maxSpeed" :maxFuel="maxFuel" :fuel="fuel" :isDoorsOpen="isDoorsOpen" />
</template>

<script>
import Speedometer from "./components/Speedometer.vue";

export default {
	name: "App",
	components: {
		Speedometer,
	},
    data: function() {
        return {
            speed: 0,
            maxSpeed: 360,
            fuel: 100,
            maxFuel: 100,
            isDoorsOpen: true,
        }
    },
    mounted: function() {
        let speedSign = 1;
        let fuelSign = -1;
        setInterval(() => {
            this.speed += 1 * speedSign;
            if((this.speed > this.maxSpeed && speedSign > 0) || (this.speed < 0 && speedSign < 0)) {
                speedSign *= -1;
            }

            this.fuel += 1 * fuelSign;
            if(this.fuel > this.maxFuel && fuelSign > 0 || this.fuel < 0 && fuelSign < 0) {
                fuelSign *= -1;
            }
        }, 10)
    }
};
</script>

<style lang="scss">
body {
	background-color: black;
}
</style>
