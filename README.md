# 启动

npm run dev

## 复现 GPU 过高的问题
- 需要在 `src/views/HomeView.vue` 中配置高德地图的 key
- 打开 chrome 中`更多工具` 中的`任务管理器`
- 点击 home 页， 加载地图, 此时 `任务管理器`中的GPU 进程在700M
- 点击 about 页，切换非地图页
- 重复以上操作5-10次， 可以看到GPU 进程飙升到 1800M 左右

