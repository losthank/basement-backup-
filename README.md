# my-first-step
1、依次显示方式：fadeIn+img（style）实现
<!DOCTYPE html>
<html>
<head>
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
</head>

<body>
<div class="aaa">
<img id="div" src="19.jpg" style="width:80px;height:80px;display:none;margin-left: 200px;margin-bottom: 100px;">
<br/>
<img id="div2" src="19.jpg" style="width:80px;height:80px;display:none;">
<br/>
</div>
</body>
</html>
