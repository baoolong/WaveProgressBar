# waveprogressbar
[![pub package](https://img.shields.io/pub/v/waveprogressbar_flutter.svg)](https://pub.dartlang.org/packages/waveprogressbar_flutter)

双平台通用,可动态调整进度，可自定义大小尺寸等

It is a good widget,can compatible with Android and IOS,Adjustable progress,Customizable color and size

如果使用当中有什么问题，请在github里提出个issues,thankYou

If there is any problem with the use, please submit an issue in github,thankYou

#### My organization's github：[https://github.com/OpenFlutter](https://github.com/OpenFlutter)

#### Contact Me ：OpenFlutter QQ群 892398530

<img width="38%" height="38%" src="https://raw.githubusercontent.com/baoolong/PullToRefresh/master/demonstrationgif/20181229_155650.gif"/>

## Usage

Add this to your package's pubspec.yaml file:

    dependencies:
	  waveprogressbar_flutter: "^0.1.1"

Add it to your dart file:

    import 'package:waveprogressbar_flutter/waveprogressbar_flutter.dart';

## Example

    import 'package:flutter/material.dart';
	import 'package:waveprogressbar_flutter/waveprogressbar_flutter.dart';

	class BezierCurveDemo extends StatefulWidget{
  		@override
  		State<StatefulWidget> createState() {
    		return BezierCurveDemoState();
  		}
	}

	class BezierCurveDemoState extends State<BezierCurveDemo>{

	  	final TextEditingController _controller = new TextEditingController();
	  	//默认初始值为0.0
	  	double waterHeight=0.0;
	  	WaterController waterController=WaterController();
	
	  	@override
	  	void initState() {
	    	super.initState();
	    	WidgetsBinding widgetsBinding=WidgetsBinding.instance;
	    	widgetsBinding.addPostFrameCallback((callback){
	      		//这里写你想要显示的百分比
	      		waterController.changeWaterHeight(0.82);
	    	});
	  	}
	
	
	  	@override
	 	Widget build(BuildContext context) {
	
	    	return new Scaffold(
	      		resizeToAvoidBottomPadding: false,
	      		appBar: new AppBar(
	        	title: new Text("贝塞尔曲线测试"),
	      	),
	      	body: new Column(
	        	children: <Widget>[
	          		new Row(
	            		children: <Widget>[
	              			new Text("高度调整:    ",
	                			style: new TextStyle(fontSize: 20.0),
	             	 		),
	              			new Container(
	                			width: 150.0,
	                			child: new TextField(
	                    			controller: _controller,
	                    			decoration: new InputDecoration(
	                      				hintText: "请输入高度",
	                    			)
	                			),
	              			),
	              			new RaisedButton(
								onPressed: (){
		                			FocusScope.of(context).requestFocus(FocusNode());
		                			waterController.changeWaterHeight(double.parse(_controller.text));
	              				},
	                			child: new Text("确定"),
	              			),
	            		],
	          		),
	          		new Container(
	            		margin: EdgeInsets.only(top: 80.0),
	            		child: new Center(
	              			child: new WaveProgressBar(
	                			flowSpeed: 2.0,
	                			waveDistance:45.0,
	                			waterColor: Color(0xFF68BEFC),
	                			heightController: waterController,
	                			percentage: waterHeight,
	                			size: new Size (300,300),
	                			textStyle: new TextStyle(
	                    			color:Color(0x15000000),
	                    			fontSize: 60.0,
	                    			fontWeight: FontWeight.bold),
	              				),
	            			),
	          			),
	        		],
	      		),
	    	);
  		}
	}

## Properties

	| size               | Size      		|   控件大小 The size of widget    	|
	| percentage         | double      		|   进度百分比 Percentage of progress	|
	| waveHeight         | double      		|   浪高 The wave height   			|
	| textStyle          | TextStyle      	|   文字样式 text style    			|
	| waveDistance       | double      		|   1/4波距 ；1/4 Wave distance    	|
	| flowSpeed          | double      		|   波浪滚动的速度 The speed of wave 	|
	| waterColor         | Color      		|   水的颜色 water color    			|
	| strokeCircleColor  | Color      		|   圆环的颜色 Stroke Circle Color   	|
	| circleStrokeWidth  | double      		|   圆环的宽度 Circle Stroke Width   	|
	| heightController   | WaterController  |   进度控制器 progress Controller   	|

