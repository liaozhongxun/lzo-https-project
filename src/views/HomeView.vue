<template>
    <div class="home">
        <button @click="gitLngLat">获取</button>
        <div>{{ data }}</div>
    </div>
</template>

<script>
export default {
    name: "HomeView",
    data() {
        return {
            data: null,
        };
    },
    methods: {
        gitLngLat() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    (res) => {
                        this.data = {
                            lat: res.coords.latitude,
                            lng: res.coords.longitude,
                        };
                    },
                    (err) => {
                        this.data = 'ERROR(' + err.code + '): ' + err.message;
                    }
                );
            } else {
                this.data = "该浏览器不支持定位";
            }
        },
    },
    mounted() {},
};
</script>
