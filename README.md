<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8" />
<title>svg animation</title>
<style>
	html, body {
		width: 100%;
		height: 100%;
		padding: 0;
		margin: 0;
	}
	body {
		background-color: rgba(100,100,100,0.2);
		overflow: hidden;
	}

	#wrapper {
		width: 100%;
		min-height: 100%;
		margin: 0 auto;
		position: relative;
	}

	#pp {
		width: 100px;
		height: 100px;
		background-color: rgba(100,0,0,0.3);
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		margin: 0 auto;
	}

	svg {
		outline: 1px solid blue;
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		margin: 0 auto;
		width: 100%;
		height: 100%;
	}
</style>
</head>

<body>
	<div id="wrapper">wrapper
		<p id="status1"></p>
		<p id="status2"></p>
		<p id="pp_size"></p>
		<div id="pp"></div>
		<svg id="mysvg" width="300" height="300"></svg>
	</div><!--/#wrapper-->
	<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
	<script>
		$(document).ready(function(){
			var d = document;
			var mysvg = d.getElementById("mysvg");
			var rand_neg;
			var rand_pos;

			setInterval(function(){
			}, 50);

			mysvg.addEventListener("mousemove", myFunction1);

			function myFunction1(e) {
				var mx = e.clientX;
				var my = e.clientY;

				var docw = $("body").width();
				var doch = $("body").height();

				var rand = {
					aa: Math.floor(Math.random()*25),
				};
				var rand_pos = Math.floor(Math.random()*25);
				var rand_neg = -(Math.floor(Math.random()*25));

				var mdpt = docw/2;
				var yini = doch -100;

				var input1 = '<path d="M'+ mdpt + ',' + yini + ' q' + ((mx-mdpt)/11) + ',' + rand_neg + ' ' + ((mx-mdpt)/11) + ',0 ' + ((mx-mdpt)/11) + ',' + rand_pos + ' ' + ((mx-mdpt)/11) + ' ' + '0 ' + ((mx-mdpt)/11) + ', ' + rand_neg + ' ' + ((mx-mdpt)/11) + ' ' + '0 ' + ((mx-mdpt)/11) + ',' + rand_pos + ' '+ ((mx-mdpt)/11) + ' 0' + ' ' + ((mx-mdpt)/11) + ',' + rand_neg + ' ' + ((mx-mdpt)/11) + ' ' + '0' + ' ' + ((mx-mdpt)/11) + ',' + rand.aa + ' ' + (((mx-mdpt)/11)*6) + ' 0" stroke="orange" stroke-width="7" fill="none">';
				$("#mysvg").html(input1);

				$("#status2").html(rand_pos + "<br>" + rand_neg);
				$("#status1").html("<strong>document size</strong><br>width: " + docw + "<br>height: " +doch);

			}
		});
	</script>
</body>
</html>
