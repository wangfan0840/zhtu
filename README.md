直接用浏览器打开index.html文件即可
	
	
	
//2.地图中心为北京市天安门 毛泽东纪念堂

//var mymap = L.map('mapid').setView([39.9012,116.39154], 15); //用这段代码，第四步就不需要了，因为缩放按钮默认显示在左上角

var mymap = L.map('mapid',{
	center: [39.9012,116.39154],//设置地图中心为北京市天安门
	zoom: 16,//设置缩放大小
	zoomControl: false //不显示缩放，后面添加缩放
});
//1.设置底图
  L.tileLayer('http://map.zhtu.net:8080/r3t-basemap/{z}/{x}/{y}/tile.jpg',{  

		   maxZoom: 18, 				                                       

 }).addTo(mymap); 
 
L.marker([39.9012,116.39154]).addTo(mymap)
	.bindPopup('<b>这是</b><br />天安门.').openPopup();

 
//3.右上角显示比例尺
L.control.scale({position: 'topright'}).addTo(mymap);

//4.左上角显示缩放按钮
L.control.zoom({position: 'topleft'}).addTo(mymap);





//5.双击地图放置一个marker，展示当前点的经度和纬度
function addPoint(e)
{
	 L.marker([e.latlng.lat, e.latlng.lng]).addTo(mymap).bindPopup('You clicked the map at <br />'+e.latlng.toString()).openPopup();
	
}
mymap.on('dblclick',addPoint);


