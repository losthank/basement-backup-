some tips about learning

call与apply是Function原型上定义的两个方法
控制台 运行出现undefined 因为函数木有返回值

http://www.csdn.net/article/2013-08-28/2816731-absolute-beginners-guide-to-nodejs
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<style type="text/css">
		img { display: block; margin-bottom: 50px; }
	</style>
</head>
<body>
<img src="-1.png" data-src="1.png">
<img src="-1.png" data-src="2.png">
<img src="-1.png" data-src="3.png">
<img src="-1.png" data-src="4.jpg">
<img src="-1.png" data-src="2.png">
<img src="-1.png" data-src="3.png">
<img src="-1.png" data-src="1.png">
<img src="-1.png" data-src="2.png">
<img src="-1.png" data-src="3.png">
<script type="text/javascript">
	/*function lazyload(){
		var imgs = document.getElementsByTagName('img');
		var n = 0;
		return function(){
			var seeHeight = window.innerHeight||document.documentElement.clientHeight||document.body.clientHeight;//兼容性考虑。准确的说三个属性值依次变小
			var scrollTop = window.scrollTop;//兼容同上，略
			for(var i = n;n<imgs.length;i+=1){
				console.log(2);
				if(imgs[i].offsetTop < seeHeight+scrollTop){//说明该图片在视图内
					if(imgs[i].getAttribute('src') ===""){
						console.log(2);
imgs[i].src = imgs[i].getAttribute('data_src');
					}
					n += 1;

				}
			}
		}
	}
	lazyload()();
	window.addEventListener('scroll',lazyload(),false);*/
	function lazyload() {
  var images = document.getElementsByTagName('img');
  var n  = 0; // 用于存储图片加载到的位置，避免每次都从第一张图片开始遍历  



  return function() {
  	 	    var seeHeight = document.documentElement.clientHeight;
    var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
    for(var i = n; i < images.length; i++) {
   
      if (images[i].offsetTop < seeHeight + scrollTop) {

        if (images[i].getAttribute('src') === '-1.png') {
        	
          images[i].src = images[i].getAttribute('data-src');
        }
        n = n + 1;
        console.log(images[3].offsetTop < seeHeight + scrollTop)
      }
    }
  }
}
lazyload(); //初始化首页的页面图片

window.addEventListener('scroll', lazyload(), false);
</script>
</body>
</html>
