some tips about learning

call与apply是Function原型上定义的两个方法
控制台 运行出现undefined 因为函数木有返回值

http://www.csdn.net/article/2013-08-28/2816731-absolute-beginners-guide-to-nodejs
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<style type="text/css">
		li{
			width: 600px;
			height: 350px;
			background-image:url(1.png);
		}
		img{
			display: block;
			overflow: hidden;
		}
	</style>
</head>
<body>
<ul>
<li><img data-src="1.jpg"></li>
<li><img data-src="2.png"></li>
<li><img data-src="3.jpg"></li>
<li><img data-src="4.jpg"></li>
<li><img data-src="5.jpg"></li>
<li><img data-src="6.jpg"></li>
<li><img data-src="7.jpg"></li>
<li><img data-src="8.jpg"></li>
</ul>
<script type="text/javascript">
//思路：考虑一下几种情况：1、顺序下拉；2、快速下拉，中间间隔的不看；3、向上滚动，看被忽略的；4、不重复加载图片
//实现上述几种：1、判断位置，窗口下不加载；2、判断滚动方向；3、判断是否已读取src
//防抖算法：定时器
  var li = document.getElementsByTagName('li');
  var images = document.getElementsByTagName('img');
  var n  = 0; // 用于存储图片加载到的位置，避免每次都从第一张图片开始遍历 
  var aa = document.documentElement.scrollTop || document.body.scrollTop;
function lazyload() {
  	var seeHeight = document.documentElement.clientHeight||window.innerHeight;//可视区域高度
    var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;//顶部滚过去的高度
    if(scrollTop>=aa){
    for(var i = n; i < images.length;i++ ) {
    if(images[i].offsetTop+li[i].offsetHeight < scrollTop)  continue;//由于加入了防抖，所以拉过头时不需要加载拉过去的全部图片，只加载当前窗口的即可
      if (images[i].offsetTop < seeHeight + scrollTop) {//说明图片在浏览器窗口
      	if(images[i].src===""){
          images[i].src = images[i].getAttribute('data-src');
          n=i;
          //console.log(n);
          }
        }else{
        	break;
        }
      }
    aa = scrollTop;//辅助判断向上还是向下滚动
  }else{//向上滚动加载之前没加载的部分
  	  for(i=n;i >0;i--) {
      if (images[i].offsetTop < seeHeight + scrollTop&&images[i].offsetTop+li[i].offsetHeight>=scrollTop) {
      	if(images[i].src===""){
          images[i].src = images[i].getAttribute('data-src');
          n=i;
          //console.log(n);
      }
}else{
	continue;
             }
        }
    }
}
lazyload(); //先运行一次，初始化首页的页面图片
function debounce(fn,delay){//防抖算法
var timer = null;
var start;
return function(){
	clearTimeout(timer);
	timer = setTimeout(function(){
		console.log(arguments);
		fn.apply(this,arguments)
	},delay);
}
}
window.addEventListener('scroll', debounce(lazyload,1000), false);

</script>
</body>
</html>
