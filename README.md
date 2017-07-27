# my-first-step
1、依次显示方式：fadeIn+img（style）实现

<script src="jquery-3.2.1.min.js"></script>
<script>
window.onload=function(){
   $("#div").fadeIn(2000);
  setTimeout('ty()',4000); 
 
} 
</script>
<script type="text/javascript">
function ty(){
	 $("#div2").fadeIn(2000);
	}
</script>
<img id="div" src="19.jpg" style="width:80px;height:80px;display:none;margin-left: 200px;margin-bottom: 100px;">
<img id="div2" src="19.jpg" style="width:80px;height:80px;display:none;">

2、<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<link rel="stylesheet" href="orange1.css">
<script language="javascript" type="text/javascript">
// 以下方式直接跳转
//window.location.href='hello.html';
// 以下方式定时跳转
setTimeout("javascript:location.href='orange2.html'", 10000000);
</script>

<script src="jquery-3.2.1.min.js"></script>
<script>
window.onload=function(){
   $("#div").fadeIn(2000);
  setTimeout('ty()',2000);//另一种方式 settimeout+setattritute
}
</script>
<script type="text/javascript">
function ty(){
	 $("#div2").fadeIn(2000);
	 setTimeout('typ()',2000);
	}
</script>
<script type="text/javascript">
function typ(){
	 $("#div3").fadeIn(2000);
	 setTimeout('changeStyle()',2000);
	}
</script>

<script type="text/javascript">

	function changeStyle(){
		$("#click").fadeIn(1000);
	    setTimeout('tt()',0);

	}
</script>

<script type="text/javascript" src="jQueryRotate.js"></script>
<script type="text/javascript">

	function tt(){
		var ti=1;
		while(ti<10000)
		{
			document.getElementById("click").style.transform="rotate(10deg)";
			ti++;

		}
	};
	
</script>

</head>

<body>


<img id="div" src="11.png" style="display:none;margin-left: 200px;margin-bottom: 100px;">
<img id="div2" src="2.png" style="display:none;margin-left: 200px;margin-bottom: 100px;">
<img id="div3" src="11.png" style="display:none;margin-left: 200px;">
<br/>


<img id="click" src="2.png" style="display:none;margin-left:200px;">


</body>
</html>
3、
@keyframes mymove
{
from {left:0px;}
to {left:200px;}
}


@-webkit-keyframes rotate{
	from{-webkit-transform:rotate(0deg)}
	to{-webkit-transform:rotate(360deg)}
	}
.image{
	
	background-repeat: no-repeat;

	-webkit-animation:9.5s linear 0s normal none infinite rotate;
	position: absolute;
	
}
