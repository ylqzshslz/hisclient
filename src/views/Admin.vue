<template>
	<div>
		<el-container>
			<el-header>Header</el-header>
			<el-container>
				<el-aside width="200px">
					<el-menu unique-opened default-active="2" class="el-menu-vertical-demo" background-color="#D3DCE6" text-color="#333" active-text-color="#ffd04b">
						<el-submenu index="1">
							<template slot="title">
								<i class="el-icon-menu"></i>
								<span>导航一</span>
							</template>
							<el-menu-item-group>
								<el-menu-item index="1-1">选项1</el-menu-item>
								<el-menu-item index="1-2">选项2</el-menu-item>
							</el-menu-item-group>
						</el-submenu>
						<el-submenu index="2">
							<template slot="title">
								<i class="el-icon-menu"></i>
								<span>导航一</span>
							</template>
							<el-menu-item-group>
								<el-menu-item index="2-1">选项1</el-menu-item>
								<el-menu-item index="2-2">选项2</el-menu-item>
							</el-menu-item-group>
						</el-submenu>
					</el-menu>
				</el-aside>
				<el-main id="main">Main</el-main>
			</el-container>
		</el-container>
	</div>
</template>

<script>
	export default {
		name: 'Admin',
		data() {
			return {
				bodyHeight: 0
			}
		},
		mounted() {
			document.getElementById('main').style.height = document.body.clientHeight - 60 + 'px';
			this.bodyHeight = document.body.clientHeight;
			window.onresize = () => {
				this.bodyHeight = document.body.clientHeight;
			}
		},
		watch: {
			bodyHeight: function() {
				document.getElementById('main').style.height = this.bodyHeight - 60 + 'px';
			}
		}
	}
</script>

<style>
	html,
	body {
		margin: 0;
		padding: 0;
		width: 100%;
		height: 100%;
	}
	
	.el-header {
		background-color: #B3C0D1;
		color: #333;
	}
	
	.el-aside {
		background-color: #D3DCE6;
		color: #333;
	}
	
	.el-main {
		background-color: #E9EEF3;
		color: #333;
	}
	
	body>.el-container {
		margin-bottom: 40px;
	}
</style>