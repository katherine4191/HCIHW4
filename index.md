<!DOCTYPE html>
<!--
Created using JS Bin
http://jsbin.com

Copyright (c) 2018 by anonymous (http://jsbin.com/dukopewixe/4/edit)

Released under the MIT license: http://jsbin.mit-license.org
-->
<meta name="robots" content="noindex">
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>MSY Calculator</title>
  
  <link href = "Resources/css/ui-lightness/jquery-ui-1.10.4.custom.min.css" rel ="stylesheet">
  <script src = "Resources/js/jquery-1.10.2.js"></script>
  <script src = "Resources/js/jquery-ui-1.10.4.custom.js"></script>
    
  <style type="text/css">
        body {
            margin: 0px 0px 0px 0px;
        }

        h1 {
            font-family: "Avant Garde", Avantgarde, "Century Gothic", CenturyGothic, "AppleGothic", sans-serif;
            font-size: 30px;
            padding: 20px 10px;
            text-align: center;
            text-transform: uppercase;
            text-rendering: optimizeLegibility;
            color: #e0dfdc;
            background-color: #333;
            letter-spacing: .1em;
            text-shadow: 
            0 -1px 0 #fff, 
            0 1px 0 #2e2e2e, 
            0 2px 0 #2c2c2c, 
            0 3px 0 #2a2a2a, 
            0 4px 0 #282828, 
            0 5px 0 #262626, 
            0 6px 0 #242424, 
            0 7px 0 #222, 
            0 8px 0 #202020, 
            0 9px 0 #1e1e1e, 
            0 10px 0 #1c1c1c, 
            0 11px 0 #1a1a1a, 
            0 12px 0 #181818, 
            0 13px 0 #161616, 
            0 14px 0 #141414, 
            0 15px 0 #121212, 
            0 22px 30px rgba(0, 0, 0, 0.9);
        }
        
        #calculator {
            font-size: 0;
            width: 330px;
			height: 590px;
            background-color:#F3F3F3; 
            padding: 20px;
            margin: auto;
			
			border-width : 10px;
			border-style : solid;
			border-color : #7ED2FF;
            border-radius: 10px;           
        }
		
		#MyCanvas{
			width: 330px;
			height: 330px;
			padding: 20px;
            margin: auto;
			align-items: center;
		}
	   
        #result {
            width: 320px;
            height: 35px;
            margin-bottom: 8px;
            padding: 0px 5px 0px 5px; // top left bottom right
            background-color: #F3F3F3;
            border-radius: 5px;
            display: inline-flex;
            justify-content: flex-end;
            align-items: center;
            overflow: hidden;
            box-shadow: inset 0 0px 3px;
            font: 20px digital;
        }
				
		#finalresult {
			width: 320px;
            height: 45px;
			margin-bottom: 10px;
            padding: 0px 5px 0px 5px;
            background-color: #F3F3F3;
            border-radius: 5px;
            display: inline-flex;
            justify-content: flex-end;
            align-items: center;
            overflow: hidden;
            box-shadow: inset 0 0px 3px;
            font: 20px digital;
		}
		
		.engineering{
			font: 20px digital;
		}
	
        .key {
            width: 59px;
            height: 20px;
            background-color: #E6E6E6;
            display: inline-flex;
            margin: 3px 5px 5px 0px;
            vertical-align: middle;
            justify-content: center;
            align-items: center;
            padding: 5px 0px 5px 0px;
			
			border-width : 0.8px;
			border-style : solid;
			border-color : #B0B0B0;
            border-radius: 4px;
            cursor: pointer;
            box-shadow: 0 3px 0 #a1a1a1, 0 2px 5px rgba(0, 0, 0, .15);
            font: bold 20px sans-serif;
        }
				
        .symbol-key {
            font: italic 20px "Times New Roman"
        }
		
		.long-symbol-key {
			width: 118px;
            font: italic 15px "Times New Roman"
        }

        .function-key {
            font: italic 15px "Times New Roman"
        }

        .eval-key {
            background-color: #B7F0B1;
            color: #62C15B;
        }
       
        .clear-key {
            background-color: #FFB2D9;
            color: #F361A6;
        }
		
		.del-key {
            background-color: #FAED7D;
            color: #FFBB00;
        }
		       
        .key:active {
            background-color: #90E4FF;
            box-shadow: 0 5px #666;
            transform: translateY(4px);
        }
		
		.btn-group button {
			padding: 5px 0px 5px 5px;
			background-color:#F3F3F3;
			align-items: center;
			
			border-width : 0.8px;
			border-style : solid;
			border-color : #B0B0B0;
            border-radius: 4px;
			float: left;
            cursor: pointer;
		}
		.button {
			position:relative;
			
			top: 110px;
			left: 280px;
			right: 308px;
			bottom: 138px;
		}
		input[type = text] {
			width : 300px;
		}
		input {
			padding: 6px;
		}
		body,html,input{
			font-family : sans-serif;
			font_size : 11pt;
		}
		form{
			margin : 20px 0;
		}
    </style>	
	
	<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjs/4.0.1/math.min.js' type='text/javascript'></script>
    
	<script src='https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.6.0/Chart.js' type='text/javascript'></script>
	<script src="Resources/js/Chart.js" type='text/javascript'></script>
	<script src='https://ajax.googleapis.com/ajax/libs/angularjs/1.6.10/angular.min.js' type='text/javascript'></script>
	<script src='https://cdn.jsdelivr.net/npm/tc-angular-chartjs@2.1.4/dist/tc-angular-chartjs.min.js' type='text/javascript'></script>
	
    <link src='https://stackpath.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css' type='text/javascript'>
	
	<link href='Resources/css/DATGUI/GUI.css' media='screen' rel='stylesheet' type='text/css'/>
	<script type='text/javascript' src='Resources/js/DATGUI/dat.gui.min.js'></script>


	
	<script type="text/javascript">
	var rangeX = [0,100];
	var term = [4,4];
	var tokens = [];
	var strFunction ="";
	var labelsValue = [];
	var dataValue1 = [];
	var dataValue2 = [];
	var funcNum = 1;
	
	
	var controls = function() {	
		this.min_X = 0;
		this.max_X = 100;
		this.term_X = 4;
		
		this.func1Col ='#FF6385';
		this.func2Col ='#4BC0C0';
		// Define render logic ...
	};
	
	var lineChart = null;		
	var lineChartData = {};
		
	$(document).ready(function(){
		var parser = math.parser();	
		var text = new controls();
		var gui = new dat.GUI();
	
		var folderX = gui.addFolder('정의역');
		var minX = folderX.add(text, 'min_X').min(-50).max(50).step(5);
		var maxX = folderX.add(text, 'max_X').min(-50).max(150).step(5);
		var termX = folderX.add(text, 'term_X').min(0).max(30).step(4);
		
		var Func1Col = gui.addColor(text, 'func1Col');
		var Func2Col = gui.addColor(text, 'func2Col');
  
		folderX.open();
		
		Func1Col.onChange(function(value){
			lineChartData.datasets[0].strokeColor = value;
			lineChartData.datasets[0].pointColor = value;
			lineChartData.datasets[0].pointStrokeColor = value;
			lineChartData.datasets[0].pointHighlightFill = value;
			lineChartData.datasets[0].pointHighlightStroke = value;
			DrawGraph();
		});
		
		Func2Col.onChange(function(value){
			lineChartData.datasets[1].strokeColor = value;
			lineChartData.datasets[1].pointColor = value;
			lineChartData.datasets[1].pointStrokeColor = value;
			lineChartData.datasets[1].pointHighlightFill = value;
			lineChartData.datasets[1].pointHighlightStroke = value;
			DrawGraph();
		});
		
		minX.onChange(function(value){
			rangeX[0] = value;
			UpdateGraph();
			
		});
		
		maxX.onChange(function(value){
			rangeX[1] = value;
			UpdateGraph();
		});
		
		termX.onChange(function(value){
			term[0] = value;
			UpdateGraph();
		});
		
		$('#BtnDraw').click(function(){
			if(tokens[0] != 'function')
				alert("입력된 함수가 없습니다.");
				
			if(funcNum == 1)
				funcNum =0;
			else if(funcNum == 0)
				funcNum = 1;
				
			var strFuncValue = '';
			var count = (rangeX[1] - rangeX[0]) / term[0] + 1;
						
			for(var i = 0 ; i < count; i++){
				labelsValue[i] = (rangeX[0] + i*term[0]).toString();
			}
			for(var i = 0 ; i < count; i++){
				strFuncValue = strFunction.substring(0,2) + labelsValue[i] + ')';
				if(funcNum == 0){
					dataValue1[i] = parser.eval(strFuncValue).toFixed(2);
				}
				else if(funcNum == 1){
					dataValue2[i] = parser.eval(strFuncValue).toFixed(2);
				}
			}
			
			lineChartData = {
				labels : labelsValue,
				datasets : [
					{
						label: "function 1",
						fillColor : "rgba(220,220,220,0.2)",
						strokeColor : '#FF6385',
						pointColor :'#FF6385',
						pointStrokeColor : '#FF6385',
						pointHighlightFill : '#FF6385',
						pointHighlightStroke : '#FF6385',
						data : dataValue1
					},
					{
						label: "function 2",
						fillColor : "rgba(151,187,205,0.2)",
						strokeColor : '#4BC0C0',
						pointColor : '#4BC0C0',
						pointStrokeColor : '#4BC0C0',
						pointHighlightFill : '#4BC0C0',
						pointHighlightStroke : '#4BC0C0',
						data : dataValue2
					}
				]
			};			
			DrawGraph();
		});
		
        
		var history = {};
		var displayValue = '0';
		var error = 'Error !! Check Syntax';			
	
		$('p').eq(0).show();
		$('#BtnEngineering').click(function(){
			if($(this).text() == '공학용'){
				$('p').eq(0).show();
				$(this).text('표준용');
			} else {
				$('p').eq(0).hide();
				$(this).text('공학용');
			}
		});
			
		$('#History_dialog').dialog({autoOpen:false});
		$('#BtnTime').click(function(){
			var historyStr = "";
			for(var key in history){ 
				historyStr += key + " = " + history[key] + "<br>";
			}
			$('#History_dialog').html(historyStr);
			$('#History_dialog').dialog('open');
		});
			
		$('#Syntax_dialog').dialog({autoOpen:false});
		$('#BtnSyntax').click(function(){
			$('#Syntax_dialog').dialog('open');
		});
			
            
        $('#result').text(displayValue);
 
        $('.key').each(function(index, key){
            $(this).click(function(e){
                if(displayValue == '0') displayValue = '';
				$('#finalresult').text('');
                if($(this).text() == 'Result'){
                    try{
						strFunction = displayValue;
                        displayValue = parser.eval(displayValue).toString();
                        tokens = displayValue.split('\(');
                        if(tokens[0] == 'function')
                        {
							strFunction;
                            displayValue = tokens[0];							
                        }
                        $('#finalresult').text(displayValue);                         
                            
						history[$('#result').text()] = displayValue;
						displayValue = '0';
                    }
                    catch (e){
                        displayValue = '0';
                        if(displayValue != 'function'){
                            $('#result').text(error);
                        }
                    }               
                }
                else
                {
                    if($(this).text() == 'AC'){
                        displayValue = '0';
                        $('#result').text(displayValue);
							$('#finalresult').text(displayValue);
                    } else if($(this).text() == 'Del'){
						displayValue = displayValue.slice(0,-1);
						$('#result').text(displayValue);
					} else if($(this).text() == 'Ans'){
						var lastKey = Object.keys(history)[Object.keys(history).length - 1];
						var lastValue = history[lastKey];
						displayValue += lastValue;
						$('#result').text(displayValue);
					} else
                    {                        
                        displayValue += $(this).text();
                        $('#result').text(displayValue);
                    }
                }
                e.preventDefault()
            })
        })
    });

	function DrawGraph() {
		if(null != lineChart)
			lineChart.clear();
		var ctx = document.getElementById("myChart").getContext("2d");
		ctx.canvas.width = 330;
		ctx.canvas.height = 330;
		lineChart = new Chart(ctx).Line(lineChartData, {
			scaleOverride:false,
			scaleShowGridLines : true,
			scaleGridLineColor : "rgba(0,0,0,0.05)",
			scaleGridLineWidth : 1,
			bezierCurve : true,
			bezierCurveTension : 0.2,
			pointDot : true,
			pointDotRadius : 3,
			pointDotStrokeWidth : 1,
			pointHitDetectionRadius : 10,
			datasetStroke : true,
			datasetStrokeWidth : 2,
			datasetFill : true
		});
	}
	
	function UpdateGraph() {
		var strFuncValue = '';
		var count = (rangeX[1] - rangeX[0]) / term[0] + 1;
		labelsValue = [];
		
		for(var i = 0 ; i < count; i++){
			labelsValue[i] = (rangeX[0] + i*term[0]).toString();
		}
		
		lineChartData = {
			labels : labelsValue,
			datasets : [
				{
					label: "function 1",
					fillColor : "rgba(220,220,220,0.2)",
					strokeColor : '#FF6385',
					pointColor :'#FF6385',
					pointStrokeColor : '#FF6385',
					pointHighlightFill : '#FF6385',
					pointHighlightStroke : '#FF6385',
					data : dataValue1
				},
				{
					label: "function 2",
					fillColor : "rgba(151,187,205,0.2)",
					strokeColor : '#4BC0C0',
					pointColor : '#4BC0C0',
					pointStrokeColor : '#4BC0C0',
					pointHighlightFill : '#4BC0C0',
					pointHighlightStroke : '#4BC0C0',
					data : dataValue2
				}
			]
		};			
		DrawGraph();
	}
	
    </script>
</head>
  
  
<body>
 <h1>
            MSY Calculator
</h1>
	<div id="MyCanvas">
		<canvas id="myChart" ></canvas>
	</div>
	<div id="calculator">
		<div class="btn-group">
			<button style="height:28px;width:28px; margin-bottom:5px; margin-left:5px" id="BtnTime"><img style="height:20px;width:20px" src="Resources/Clock.png"></button>
			<div id="History_dialog" title = "History Dialog"></div>
			<button style="height:28px;width:56px; margin-bottom:5px; margin-left:5px" id="BtnSyntax">Syntax</button>
			<div id="Syntax_dialog" title = "Syntax Dialog">
				1. 행렬 계산 <br>
				- 곱셈 * <br>
				var a = math.complex(2, 3) <br>
				var b = math.complex(4, 1) <br>
				math.multiply(a, b) <br>
				// returns Array [[7, -6, 17], [13, -4, 33]] <br>
				- 역행렬 inv <br>
				inv([[1, 2], [3, 4]]) <br>
				// returns [[-2, 1], [1.5, -0.5]] <br>
				2. 내적 dot <br>
				- dot([2, 4, 1], [2, 2, 3]) <br>
				// returns number 15 <br>
				3. 외적 cross <br>
				- cross([1, 1, 0],   [0, 1, 1]) <br>
				// Returns [1, -1, 1] <br>
				- cross([3, -3, 1],  [4, 9, 2]) <br>
				// Returns [-15, -2, 39] <br>	
			</div>
		
			<button style="height:28px;width:98px; margin-bottom:5px; margin-left:5px" id="BtnDraw">DrawFunction</button>
		</div>
		
		<div id="result">0</div>
		<div id="finalresult">0</div>
		<button id="BtnEngineering">표준용</button>
		
		<br>
        <p>
			<span class="key function-key">inv</span>
			<span class="key long-symbol-key">factorial</span>
			<span class="key">==</span>
			<span class="key">!=</span>
			
			<span class="key"><</span>
			<span class="key">></span>
			<span class="key"><=</span>
			<span class="key">>=</span>
			<span class="key clear-key">AC</span>

			<span class="key function-key">det</span>
			<span class="key function-key">log</span>
			<span class="key function-key">exp</span>
			<span class="key function-key">sqrt</span>
			<span class="key">^</span>
			
			<span class="key function-key">sin</span>
			<span class="key function-key">cos</span>
			<span class="key function-key">tan</span>
			<span class="key function-key">cross</span>
			<span class="key function-key">dot</span>		
			
		</p>
		<span class="key">=</span>
		<span class="key">(</span>
        <span class="key">)</span>
		<span class="key">[</span>
		<span class="key">]</span>
        
		
		<span class="key symbol-key">x</span>
		<span class="key symbol-key">y</span>
		<span class="key symbol-key">z</span>
		<span class="key symbol-key">f</span>
		<span class="key symbol-key">g</span>
			
        <span class="key">7</span>
        <span class="key">8</span>
        <span class="key">9</span>
		<span class="key">%</span>
		<span class="key del-key">Del</span>
        <span class="key">4</span>
        <span class="key">5</span>
        <span class="key">6</span>		
        <span class="key">+</span>
        <span class="key">-</span>
		<span class="key">1</span>
		<span class="key">2</span>
		<span class="key">3</span>
		<span class="key">/</span>
		<span class="key">*</span>
		<span class="key">0</span>
        <span class="key">.</span>
		<span class="key">,</span>
		<span class="key">Ans</span>
		<span class="key eval-key">Result</span>
		
		<span class="key symbol-key">i</span>
        <span class="key symbol-key">e</span>
        <span class="key symbol-key">pi</span>
		<span class="key">:</span>
		<span class="key">;</span>
    </div>
  </body>
</html>
