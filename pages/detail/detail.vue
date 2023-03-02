<template>
	<view class="">
	<!-- 	<text>唱歌跳舞打篮球</text>
		<text selectable>唱歌跳舞打篮球</text >
		<text selectable space="ensp">唱歌      跳舞  打篮球</text >
		<text selectable space="emsp">唱歌      跳舞  打篮球</text >
		<text selectable space="nbsp" style="font-size: 100px;">唱歌      跳舞  打篮球</text >
		<text decode>唱歌&lt;&lt;跳舞  打篮球</text > -->
		<!-- <view class="box" hover-class="box-active">我是一个大盒子</view> -->
		<view class="box2" hover-class="box2-active">	
		<!-- hover-stop-propagation 阻止冒泡 -->
		  <view class="box" hover-class="box-active" hover-stay-time="2000" hover-stop-propagation hover-start-time="2000">
			   我是一个大盒子
			</view>
		</view>
	</view>
</template>

<script>
</script>

<style  lang="scss">
	
	.box2{
		width: 200px;
		height: 200px;
		background-color: blue;
	}
	.box2-active{
		background-color: pink;
	}
	.box{
		width: 100px;
		height: 100px;
		background-color: green;
	}
	.box-active{
		background-color: red;
	}
</style>