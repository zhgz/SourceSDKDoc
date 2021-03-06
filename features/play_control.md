#3、投屏及控制
投屏首先要建立连接，可以参考[2、建立连接](/features/connect.md)

## 1）设置播控监听
```java
ILelinkPlayerListener playerListener = new ILelinkPlayerListener() {

        /**
        * 播放开始
        */
        @Override
        public void onStart() {

        }

        /**
        * 暂停
        */
        @Override
        public void onPause() {

        }

        /**
        * 播放完成
        */
        @Override
        public void onCompletion() {

        }

        /**
        * 播放结束
        */
        @Override
        public void onStop() {

        }

        /**
        * 进度调节：单位为百分比
        */
        @Override
        public void onSeekComplete(int pPosition) {

        }

        /**
        * 保留接口
        */
        @Override
        public void onInfo(int what, int extra) {

        }

        /**
        * 错误回调
        */
        @Override
        public void onError(int what, int extra) {

        }

        /**
        * 音量变化回调
        */
        @Override
        public void onVolumeChanged(float percent) {

        }

        /**
        * 播放进度信息回调
        * @param duration 总长度：单位秒
        * @param position 当前进度：单位秒
        */
        @Override
        public void onPositionUpdate(long duration, long position) {

        }

};
lelinkPlayer.setPlayerListener(lelinkPlayerListener);
```
关于onError的what有下列取值
- ILelinkPlayerListener.PUSH_ERROR_INIT：推送初始化错误
- ILelinkPlayerListener.PUSH_ERROR_PLAY：推送播放错误
- ILelinkPlayerListener.MIRROR_ERROR_INIT：镜像初始化错误
- ILelinkPlayerListener.MIRROR_ERROR_PREPARE：镜像准备错误
- ILelinkPlayerListener.MIRROR_ERROR_CODEC：镜像编码错误

## 2）推送媒体(开始播放)
```java
// 实例化播放的媒体信息
LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
// 设置媒体类型：LelinkPlayerInfo.TYPE_VIDEO：视频
//              LelinkPlayerInfo.TYPE_AUDIO：音乐
//              LelinkPlayerInfo.TYPE_IMAGE：图片
lelinkPlayerInfo.setType(LelinkPlayerInfo.TYPE_VIDEO);
// 设置本地文件path，支持本地推送
// lelinkPlayerInfo.setLocalPath(localurl);
// 设置网络url，支持网络推送，与本地推送二选一
lelinkPlayerInfo.setUrl(url);
leLinkPlayer.setDataSource(lelinkPlayerInfo);
leLinkPlayer.start();
```
##3）暂停
```java
leLinkPlayer.pause();
```
##4）恢复播放
```java
leLinkPlayer.resume();
```
##5）停止
```java
leLinkPlayer.stop();
```
##6）播放进度控制
```java
leLinkPlayer.seekTo(progress);
```
progress的单位为秒

<!--
##7）音量控制
```java
leLlinkPlayer.setVolume(percent);
```
percent（百分比，float类型）的取值范围为0~1
-->
##7）增加音量
```java
leLinkPlayer.addVolume();
```
##8）减少音量
```java
leLinkPlayer.subVolume()
```
## 9） 直接推送
```java
LelinkPlayerInfo lelinkPlayerInfo = new LelinkPlayerInfo();
lelinkPlayerInfo.setLelinkServiceInfo(mLelinkServiceInfo);
lelinkPlayerInfo.setType(LelinkPlayerInfo.TYPE_VIDEO);
lelinkPlayerInfo.setUrl(url);
//lelinkPlayerInfo.setLocalPath(url);
leLinkPlayer.setDataSource(lelinkPlayerInfo);
leLinkPlayer.start();
```

PS:SDK中关于两种模式的区别是判断是否设置了**setLelinkServiceInfo()**，如果mLelinkServiceInfo不为空，则认为是直接推送，如果为空，则认为是先连接了后在推送
<!--
##是否支持弹幕
```java
leLinkPlayer.isSupportDanmuku();
```
-->

<!--
##发送弹幕
```java
DanmukuInfo danmukuInfo = new DanmukuInfo();
danmukuInfo.setAplha(aplha);
danmukuInfo.setContent(text);
danmukuInfo.setFontsize(size);
leLinkPlayer.sendDanmuku(danmukuInfo);
```
-->











