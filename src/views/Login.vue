<template>
	<div>
		<el-card class="box-card">
			<div slot="header" class="clearfix">
				<span>东软云HIS医院管理系统 登录</span>
			</div>
			<div class="text item">
				<el-form ref="user" :model="user" label-width="60px">
					<el-form-item label="用户名">
						<el-input v-model.trim="user.userName"></el-input>
					</el-form-item>
					<el-form-item label="密码">
						<el-input v-model.trim="user.password" show-password></el-input>
					</el-form-item>
					<el-form-item>
						<el-button type="primary" @click="login()">登录</el-button>
					</el-form-item>
				</el-form>
			</div>
		</el-card>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				user: {
					userName: '',
					password: ''
				}
			}
		},
		methods: {
			login() {
				if(this.user.userName == ''){
					alert('用户名不能为空!');
					return;
				}
				if(this.user.password == ''){
					alert('密码不能为空!');
					return;
				}
				this.$axios.post('selectUserByUserNameByPassword', this.user)
					.then((response) => {
						if(response.data == ''){
							alert('用户名或密码错误!');
						}else{
							this.$setSessionStorage('user', response.data);
							this.$router.push('/admin');
						}
					})
					.catch((error) => {
						alert('登录请求失败!');
						console.log(error);
					});
			}
		}
	}
</script>

<style scoped>
	.text {
		font-size: 14px;
	}
	
	.item {
		margin-bottom: 18px;
	}
	
	.clearfix:before,
	.clearfix:after {
		display: table;
		content: "";
	}
	
	.clearfix:after {
		clear: both
	}
	
	.box-card {
		width: 400px;
		margin: 0 auto;
		margin-top: 150px;
	}
</style>