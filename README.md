# Geolocation
效果：https://xl-z4869.github.io/Geolocation/index.html

使用浏览器内置Web Geolocation API，将获取到的地理位置及相关坐标，实现指南针旋转和速度的变化
### 一、知识点
Web Geolocation  
https://developer.mozilla.org/zh-CN/docs/Web/API/Geolocation
#### 1.getCurrentPosition()和watchPosition()方法f法fs'dfsd
* getCurrentPosition()方法在调用时返回一次相关信息
* watchPosition()方法调用后将持续返回相关信息
* 两个方法调用时除了传入相关的回调函数外，还需要传入options作为第三个参数，相关键值如下：
   * enbleHighAccuracy参数是否高精度可用，为布尔类型，默认为false，如果开启，响应时间会变慢，同时，在手机设备上会用掉更多的流量

   * timeout表示等待响应的最大时间，默认是0毫秒，表示无穷时间

   *  maximumAge表示应用程序的缓存时间，单位毫秒，默认是0，也就是每次请求都是立即去获取一个全新的对象内容
### 二、主要步骤
#### 1.使用getCurrentPosition()方法调用相关信息
```
navigator.geolocation.getCurrentPosition(success, error, options);
```
#### 2.成功之后返回结果时，将获得的信息赋给对应的元素
```
function success(pos) {
    var crd = pos.coords;
    console.log(pos);
    console.log('Your current position is:');
    console.log('Latitude : ' + crd.latitude);
    console.log('Longitude: ' + crd.longitude);
    console.log('More or less ' + crd.accuracy + ' meters.'
    console.log(crd.speed);
    //直接赋值查看效果
    speed.innerHTML = 12
    arrow.style.transform = `rotate(45deg)`
    
    //实际情况
    speed.innerHTML = crd.speed;
    arrow.style.transform = `rotate(${crd.heading}deg)`;
};
```
