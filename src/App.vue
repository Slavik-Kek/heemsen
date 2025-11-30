<template>
  <div class="drawtools">
    <button class="tools" id="draw">Draw</button>
    <button class="tools" id="erase">Erase</button>
    <button class="tools" id="select">Select & Move</button>
  </div>
  <div id="mapContainer"></div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";

export default{
  name: "KZL PLaner",
  data() {
    return{
      map: null
    };
  },
  mounted(){
    this.map = L.map("mapContainer").setView([52.70806, 9.25532], 16);
    L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
    }).addTo(this.map);
    var customPane = this.map.createPane("customPane");
    var canvasRenderer = L.canvas({ pane: "customPane" });
    customPane.style.zIndex = 399;

    var marker = L.marker([52.70806,9.25532]).addTo(this.map);
    var marker_2 = L.marker([52.708004,9.25530]).addTo(this.map);
  },
  onBeforeUnmount() {
    if (this.map) {
      this.map.remove();
    }
  }
};
</script>

<style scoped>
#mapContainer {
  width: 100%;
  height: 800px;
}

.drawtools {
    margin: auto;
    width: 50%;
    /*border: 1px;*/
    display: -webkit-box;
    display: -moz-box;
    display: -ms-flexbox;
    display: -webkit-flex;
    display: flex;
}

.tools {
    /*text-align:center;
    border: 5px;*/
    max-width: 10%;
    -webkit-box-flex: 1 1 auto;
    -moz-box-flex:  1 1 auto;
    -webkit-flex:  1 1 auto;
    -ms-flex:  1 1 auto;
    flex:  1 1 auto;
}
</style>
