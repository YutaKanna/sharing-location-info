// resources/js/components/LocationMap.vue
<template>
  <div>
    <h1>位置情報共有アプリ</h1>
    <GmapMap
      :center="{ lat: latitude, lng: longitude }"
      :zoom="13"
      style="width: 100%; height: 400px"
    >
      <GmapMarker :position="{ lat: latitude, lng: longitude }"></GmapMarker>
    </GmapMap>
    <button @click="getLocation">現在の位置を取得</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      latitude: 0,
      longitude: 0
    };
  },
  methods: {
    getLocation() {
      if ("geolocation" in navigator) {
        navigator.geolocation.getCurrentPosition((position) => {
          this.latitude = position.coords.latitude;
          this.longitude = position.coords.longitude;
        });
      } else {
        alert("このブラウザは位置情報をサポートしていません。");
      }
    }
  }
};
</script>

<style scoped>
/* スタイルを追加することもできます */
</style>
