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
	var li = document.getElementsByTagName('li');
  var images = document.getElementsByTagName('img');
  var n  = 0; // 用于存储图片加载到的位置，避免每次都从第一张图片开始遍历 
function lazyload() {
  	var seeHeight = document.documentElement.clientHeight||window.innerHeight;//可视区域高度
    var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;//顶部滚过去的高度
    for(var i = n; i < images.length; i++) {
    if(images[i].offsetTop < scrollTop) continue;//由于加入了防抖，所以拉过头时不需要加载拉过去的全部图片，只加载当前窗口的即可
      if (images[i].offsetTop < seeHeight + scrollTop) {//说明图片在浏览器窗口
          images[i].src = images[i].getAttribute('data-src');
          n = n + 1;
        }else{
        	break;
        }
      }
    }

lazyload(); //先运行一次，初始化首页的页面图片

window.addEventListener('scroll', debounce(lazyload,1000), false);

function debounce(fn,delay){
var timer = null;
var start;
return function(){
	clearTimeout(timer);
	timer = setTimeout(function(){
		fn.apply(this,arguments)
	},delay);
}
}
</script>
</body>
</html>
if(images[i].offsetTop+li[i].offsetHeight < scrollTop)   注意倒着滚动 是从n开始执行的 会卡住
