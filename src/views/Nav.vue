<template>
	
	
	<div>
		<ul class="nav-list" style="background: #C6E2FF;">
		<img src="../assets/image/zhihu.png" style="margin-left: 320px; margin-right:10px; height: 40px;" />
		<li class="nav-item"><router-link to="/home">首页</router-link></li>
		<li class="nav-item"><router-link to="/explore">发现</router-link></li>
		<li class="nav-item"><router-link to="/question/waiting">等你来答</router-link></li>
		<li class="nav-item2" ><router-link to="/login" style="margin-left:100px;">登录</router-link></li>
		</ul>
		
	<router-view />
	</div>
</template>

<script>
	export default{
		name:'Navbar',
		data() {
			return{};
		},
		created() {}
	};
</script>

<style lang="scss" scoped>
	
	 //大导航栏的样式 
	.nav-list{
		background-color:white;
		height: 50px;
		width: 100%;
		display: flex;
		align-items: center;
		box-shadow: 2px 5px 5px #aaa;
		align-items: center;
		
		
	}
	
	.container img{
		height: 100%;
		width: auto;
		margin-right: 30px;
		margin-left: 500px;
	}
	.nav-item {
		width: 5%;
		font-size: 14px;
		
	}
	
</style>