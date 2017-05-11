#  地图API-静态图

如何在页面中使用地图的图片？现在百度地图已经提供完整的API使用：

百度地图静态图API，可实现将百度地图以图片形式嵌入到您的网页中。您只需发送HTTP请求访问百度地图静态图服务，便可在网页上以图片形式显示您的地图。静态图API较之JavaScript API载入的动态网站，既能满足基本的地图信息浏览，又能加快网页访问速度。
	
代码：

```
http://api.map.baidu.com/staticimage/v2?ak=GjxqD6pWKb9opUIWD5TiSAH4PZdvPNaj&mcode=666666&center=116.403874,39.914888&width=300&height=200&zoom=9
```
参数解析：
	
1. ak参数：注册用户的认证信息，用户的访问密钥。申请地址：<a href="http://lbsyun.baidu.com/apiconsole/key" target="_blank">传送门</a>，比如：GjxqD6pWKb9opUIWD5TiSAH4PZdvPNaj
2. mcode：安全码。若为Android/IOS SDK的ak, 该参数必需。
3. width 默认400 图片宽度。取值范围：(0, 1024]。Scale=2,取值范围：(0, 512]。
height 默认300 图片高度。取值范围：(0, 1024]。Scale=2,取值范围：(0, 512]。
4. center：地图中心点位置，参数可以为经纬度坐标或名称。坐标格式：lng<经度>，lat<纬度>，例如116.43213,38.76623。
5. zoom：地图级别。高清图范围[3, 18]；低清图范围[3,19]
6. &copyright=1 去掉百度logo
7. &scale=2 默认为null,返回图片大小会根据此标志调整。取值范围为1或2：
1表示返回的图片大小为size= width * height;
2表示返回图片为(width*2)*(height *2)，且zoom加1
注：如果zoom为最大级别，则返回图片为（width*2）		minutes*（height*2），zoom不变。
	
其他参数：
<img src="https://raw.githubusercontent.com/siwenyu/img/master/%E9%9D%99%E6%80%81%E5%9C%B0%E5%9B%BEAPI.png">

在线文档：<a href="http://lbsyun.baidu.com/index.php?title=%E9%A6%96%E9%A1%B5" target="_blank">首页</a>


	