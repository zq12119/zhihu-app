<template>
	
	<div style="margin: 0 auto;">
		<div class="container" style="margin-left: 300px;">
			<div class="head">
				<img class="pic-all1" src="../assets/image/special.png" />

				<h2 style="margin-top: 20px; margin-bottom: 20px; font-size: 30px;">最新专题</h2>
			</div>
			<!-- 显示内容 -->
			<div class="row">
				<div class="card1" v-for="(item, index) in specials" :key="index">
					<!--图片 -->
					<img :src="item.banner" alt="" />
					<div class="w-row">
						<div class="left">
							<!-- 标题 -->
							<h3>{{ item.title }}</h3>
							<!-- 小字 -->
							<span style="color: #8590A6;font-size: 12px;" class="meta">{{ item.updated }}更新·{{ item.viewCount }}浏览</span>
						</div>
						<div class="right">
							<!-- 关注按钮 -->
							<button class="button">
								<h3>关注专题</h3>
							</button>

						</div>

					</div>
					<div>
						<!-- 水平线 -->
						<hr style="border: 1px solid #E5E5E5;color: #E5E5E5; width: 90%; margin: 0 auto;">
						<!-- 因没有标签和概括内容这里是描述 -->
						<p class="introduction">{{ item.introduction }}</p>

					</div>

				</div>
			</div>
			<!-- 查看更多：使其跳转到全部专题页面 -->
			<div class="topic" style="margin-left: -70px;">
				<router-link to="/special/all" class="btn"><button class="button-topic">
						<h3 style="color: #A9A9A9;">查看更多专题 ></h3>
					</button></router-link>
			</div>

		</div>


		<!-- 圆桌讨论 -->
		<div class="container1" style="margin-left: 300px;">
			<div class="head">
				<!-- 图标 -->
				<img class="pic-roundtable" src="../assets/image/roundtable.png" />
				<h2 style="margin-top: 20px; margin-bottom: 20px;margin-left: 10px; font-size: 30px;">圆桌讨论</h2>
			</div>

			<div class="row">
				<div class="roundtable" v-for="(item, index) in roundtable" :key="index">
					<div class="w-row">
						<div class="shadow">
						</div>
						<img :src="item.banner" alt="" />
					</div>
					<div class="w-row">
						<div class="round-left">
							<h3>{{item.name }}</h3>
							<div class="a">
								<h5>
									进入21世纪以后，随着科学技术特别是计算机技术、数字化与图像识别技术、
									人工神经网络技术和机电一体化技术的大发展...
								</h5>
							</div>
							<h5 class="concern">{{item.includeCount}}位嘉宾参与 | {{item.visitsCount}}人关注</h5>
						</div>
						<div class="round-right">
							<button class="button">
								<h4>关注圆桌</h4>
							</button>
						</div>
					</div>
					
					<h4 style="margin-left: 10px;margin-top: 20px;">做CT检查时如果体内有金属会对检查结果产生什么影响？</h4>
					<br />
					<h5 style="color: darkgray;margin-left: 10px;">450个回答</h5>
					
				</div>
			</div>
		</div>
		<div class="topic" style="margin-left: 50px;">
			<router-link to="/roundtable" class="btn"><button class="button-topic">
					<h3 style="color: #A9A9A9;">查看更多圆桌 ></h3>
				</button></router-link>
		</div>		
	</div>
</template>

<script>
export default {
	name: 'hot',
	data() {
		return {
			specials: [],
			roundtable: []
		};
	},
	created() {
//圆桌的接口获取
		this.axios.get('http://localhost:8080/api/roundtable').then(res => {
					console.log(res);
					this.roundtable = res.data.data;
				});
	//最新专题的接口获取
		this.axios.get('http://localhost:8080/api/special').then(res => {
			console.log(res);
			this.specials = res.data.data;
		});
	   
	}
};
</script>

<style lang="scss" scoped>
@font-face {
	font-family: 'iconfont'; 
	src: url('//at.alicdn.com/t/font_1616266_b8gknsgz736.eot');
	src: url('//at.alicdn.com/t/font_1616266_b8gknsgz736.eot?#iefix') format('embedded-opentype'), url('//at.alicdn.com/t/font_1616266_b8gknsgz736.woff2') format('woff2'),
		url('//at.alicdn.com/t/font_1616266_b8gknsgz736.woff') format('woff'), url('//at.alicdn.com/t/font_1616266_b8gknsgz736.ttf') format('truetype'),
		url('//at.alicdn.com/t/font_1616266_b8gknsgz736.svg#iconfont') format('svg');
}
.iconfont {
		font-family: 'iconfont' !important;
		font-size: 30px;
		font-style: normal;
		-webkit-font-smoothing: antialiased;
		-webkit-text-stroke-width: 0.2px;
		-moz-osx-font-smoothing: grayscale;
		color: blue;
		margin: 10px;
	}
	.row {
		margin: 0 auto;
		display: flex;
		flex-wrap: wrap;
		border-radius: 10px;
	}
	.container {
		display: block;
		margin: auto;
		width: 70%;
		margin-top: 15px;
	}
	.head {
		display: flex;
		align-items: center;
	}
	.a {
	margin-top: 15px;
	height: 54px;
	width: 100%;
	text-overflow: -o-ellipsis-lastline;
	overflow: hidden;
	text-overflow: ellipsis;
	display: -webkit-box; /*重点，不能用block等其他*/
	-webkit-line-clamp: 3; /*重点IE和火狐不支持*/
	-webkit-box-orient: vertical; /*重点*/
}
	.card1 {
		box-shadow: 2px 5px 5px #aaa;
		width: 44%;
		margin: 1%;
		height: 440px;
		background-color: rgb(255, 255, 255);
	}
	.card1 img {
		border-radius: 5px;
		width: 100%;
		height: 200px;
	}
	.left {
		height: 100px;
		width: 80%;
		padding: 25px;
	}
	.left h5 {
		color: darkgray;
	}
	.right {
		height: 100px;
		width: 20%;
		padding-top: 30px;
	}
	.button {
		width: 90%;
		border: none;
		background-color: rgb(235, 245, 255);
		color: rgb(30, 134, 255);
		height: 40px;
		border-radius: 5px;
	}
	.introduction {
		margin: 20px;
		text-indent: 50px;
	}
	.topic {
		margin-top: 20px;
		height: 100px;
		text-align: center;
		margin-left: -35px;
	}
	.button-topic {
		border: none;
		width: 160px;
		background-color: rgb(255, 255, 255);
		height: 50px;
		border-radius: 50px;
	}
	.section {
		float: left;
		background-color: rgb(246, 246, 246);
		width: auto;
		margin-right: 10px;
		padding: 2px;
		font-size: 13px;
		border-radius: 5px;
		height: auto;
	}
	.section1 {
		background-color: rgb(246, 246, 246);
		width: auto;
		margin-right: 10px;
		padding: 2px;
		font-size: 13px;
		border-radius: 5px;
	}
	.container1 {
		display: block;
		margin: 0 auto;
		width: 70%;
		margin-top: 15px;
	}
	// 圆桌卡片样式
	.roundtable {
		box-shadow: 2px 5px 5px #aaa;
		width: 44%;
		margin: 1%;
		height: 360px;
		background-color: rgb(255, 255, 255);
		position: relative;
	}
	.roundtable img {
		border-radius: 5px;
		width: 50%;
		height: 50%;
		position: absolute;
		right: 0;
	}
	.shadow {
		z-index: 10;
		width: 100%;
		height: 220px;
		text-align: center;
		background-image: linear-gradient(to right, #e66465, #9198e5, rgba(255, 255, 255, 0));
	}
	.round-left {
		position: absolute;
		top: 70px;
		left: 25px;
		width: 70%;
		color: white;
		z-index: 11;
	}
	.a {
		margin-top: 15px;
		height: 65px;
		width: 100%;
	}
	.concern {
		margin-left: 80px;
		margin-top: 80px;
	}
	.round-right {
		position: absolute;
		top: 160px;
		right: 0;
		width: 23%;
	}
	.container2 {
		display: block;
		margin: auto;
		width: 70%;
		margin-top: 15px;
	}
</style>