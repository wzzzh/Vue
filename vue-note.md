### Vue学习笔记 ###
##  ##
一、vue的基本语法：
	  
	1.创建一个Vue的实例化对象  
		new Vue({
			el:'#app',
			data:{
				val:'',
				arr:[1,2,3]
			},
			methods:{
				click(){
					alert(1)
				}
			}
		})
	注：el:用于挂载当前组件的一个容器的名字：例如：id="app"->el:'#app',class ="app"->el:'.app'
		data:初始化数据的存放地
		methods:事件存放地，多个事件间用，分隔

1.模板语法：  

	**指令：**
	1.数据绑定通过{{val}}
	2.v-html与v-text:
			将数据以htm || text的形式体现，如果是v-html则会自动识别数据的标签只显示标签中的内容，如果text则会将数据作文本形式解析
		例：
			html部分:
				1.	<li v-html ="ht"></li>
						此时渲染后的结构为：
						<li>
							<span>你想让我是什么</span>
						</li>
				
				2.	<li v-text ="ht"></li>
						此时渲染后的结构为：
						<li><span>你想让我是什么</span></li>	
					ht这个数据作为li的文本内容显示了
			js部分：
			new Vue({
	          el:'#myPro',
	          data:{
	            ht:'<span>你想让我是什么</span>'
	          },
	        })
	3.v-bind:用于改变css和style
	  简写->:
	  例如：
		html部分：
			<button :class="{active:active} @click="changColor">点击变色</button>
	      	<div id="box" :style="{background:color} v-show="show_hide""></div>
		js部分：
			new Vue({
	          el:'#myPro',
	          data:{
	            color:'red',
				active:false
				show_hide:false
	          },
	          methods:{
	            changColor(){
					this.active=true;
					this.show_hide=true;
	              if(this.color=='red'){
	                this.color='pink'
	              }else{
	                this.color='red'
	              }	
	            }
	          }
	        })
	4.v-show，通过检测v-sho里边布尔值的真假，控制元素的显示和隐藏。例子如上
		