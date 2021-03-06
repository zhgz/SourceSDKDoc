# 1、服务搜索

## 1) 设置搜索监听
```java
private IBrowseListener browserListener = new IBrowseListener() {

       @Override
       public void onBrowse(int resultCode, List<LelinkServiceInfo> list) {

       }

};
```
browseListener 为服务搜索监听
```java
mLelinkServiceManager.setOnBrowseListener(browseListener);
```
参数代表的意义：
- resultCode:
       - IBrowseListener.BROWSE_SUCCESS：搜索成功
       - IBrowseListener.BROWSE_ERROR_AUTH：搜索失败，**Auth错误，请检查您的网络设置或AppId和AppSecret**
- list：搜索出来的结果信息，请根据这个结果信息来显示搜索到的设备列表。

**PS：onBrowse是在子线程工作，以下接口回调，如无特殊说明，都是在子线程回调**

## 2) 开始搜索
```java
mLelinkServiceManager.browse(int browserType);
```

其中browserType的取值为以下几种类型:

* ILelinkServiceManager.TYPE\_ALL：可以搜索到乐联和DLNA协议
* ILelinkServiceManager.TYPE\_LELINK：仅搜索乐联协议
<!--* ILelinkServiceManager.TYPE\_DLNA：仅搜索DLNA协议-->

## 3）停止搜索
```java
mLelinkServiceManager.stopBrowse();
```

## 4）LelinkServiceInfo参数说明
###name
```java
lelinkServiceInfo.getName();
```
设备名称
###ip
```java
lelinkServiceInfo.getIp();
```
获取接收端的ip
###isOnLine
```java
lelinkServiceInfo.isOnLine();
```
代表设备是否在线（指设备是否能连接到）;
true为在线，false为不在线
###isConnect
```java
lelinkServiceInfo.isConnect();
```
代表该设备是否已经连接。
true为已连接，false为没连接。
