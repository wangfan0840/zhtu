ֱ�����������index.html�ļ�����
	
	
	
//2.��ͼ����Ϊ�������찲�� ë�󶫼�����

//var mymap = L.map('mapid').setView([39.9012,116.39154], 15); //����δ��룬���Ĳ��Ͳ���Ҫ�ˣ���Ϊ���Ű�ťĬ����ʾ�����Ͻ�

var mymap = L.map('mapid',{
	center: [39.9012,116.39154],//���õ�ͼ����Ϊ�������찲��
	zoom: 16,//�������Ŵ�С
	zoomControl: false //����ʾ���ţ������������
});
//1.���õ�ͼ
  L.tileLayer('http://map.zhtu.net:8080/r3t-basemap/{z}/{x}/{y}/tile.jpg',{  

		   maxZoom: 18, 				                                       

 }).addTo(mymap); 
 
L.marker([39.9012,116.39154]).addTo(mymap)
	.bindPopup('<b>����</b><br />�찲��.').openPopup();

 
//3.���Ͻ���ʾ������
L.control.scale({position: 'topright'}).addTo(mymap);

//4.���Ͻ���ʾ���Ű�ť
L.control.zoom({position: 'topleft'}).addTo(mymap);





//5.˫����ͼ����һ��marker��չʾ��ǰ��ľ��Ⱥ�γ��
function addPoint(e)
{
	 L.marker([e.latlng.lat, e.latlng.lng]).addTo(mymap).bindPopup('You clicked the map at <br />'+e.latlng.toString()).openPopup();
	
}
mymap.on('dblclick',addPoint);


