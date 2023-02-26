<script setup lang="ts">
import { onBeforeUnmount } from 'vue'
import AMapLoader from '@amap/amap-jsapi-loader'

window.forceWebGL = true

let map = null
let mapToolBar = null
let mapScale = null
let mapType = null

AMapLoader.load({
  key: '', // 申请好的Web端开发者Key，首次调用 load 时必填
  version: '2.0', // 指定要加载的 JSAPI 的版本，缺省时默认为 1.4.15
  plugins: [
    'AMap.ToolBar',
    'AMap.Scale',
    'AMap.Overview',
    'AMap.MapType',
    'AMap.Geolocation'
  ], // 需要使用的的插件列表，如比例尺'AMap.Scale'等
  Loca: {
    version: '2.0'
  },
  AMapUI: {
    version: '1.1',
    plugins: []
  }
})
  .then((AMap) => {
    window.AMapUI.load(
      ['ui/misc/PathSimplifier'],
      function (PathSimplifier: any) {
        window.AMapUI.PathSimplifier = PathSimplifier
      }
    )
    window.AMapUI.load(
      ['ui/misc/PointSimplifier'],
      function (PointSimplifier: any) {
        window.AMapUI.PointSimplifier = PointSimplifier
      }
    )
    window.AMapUI.loadUI(
      ['control/BasicControl'],
      function (BasicControl: any) {
        window.AMapUI.BasicControl = BasicControl
      }
    )
    map = new AMap.Map('map-container')
    let styleName = 'amap://styles/whitesmoke'
    mapToolBar = new window.AMap.ToolBar()
    mapScale = new window.AMap.Scale()
    mapType = new window.AMap.MapType({ showTraffic: true })
    map.setMapStyle(styleName)
    map.addControl(mapToolBar)
    map.addControl(mapScale)
    map.addControl(mapType)
  })
  .catch((e) => {
    console.log(e)
  })

onBeforeUnmount(() => {
  console.log(222)
  map.removeControl(mapToolBar)
  map.removeControl(mapScale)
  map.removeControl(mapType)
  map?.clearMap()
  map?.destroy()
})
</script>

<template>
  <main>
    <!-- <TheWelcome /> -->
    <div>
      222
      <div id="map-container">12</div>
    </div>
  </main>
</template>

<style>
#map-container {
  width: 800px;
  height: 500px;
}
</style>
