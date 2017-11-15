# vue-route
vue-route
<!DOCTYPE html>
<html lang="en">

	<head>
		<meta charset="UTF-8">
		<title>VueJS</title>
		<script src="js/vue.min.js"></script>
		<script src="js/vue-route.js"></script>
	</head>
	<body>
		<div id="app">
			<router-link to="/user/parent">Go to parnet</router-link>
			<router-link to="/user/parent/profile">Go to child-profile</router-link>
			<router-link to="/user/parent/posts">Go to child-posts</router-link>
			<router-view></router-view>
		</div>
		<script>
			const User = {
				template: '<div class="user"><h2>User {{$route.params.id}}</h2><router-view></router-view></div>'
			};
			const UserProfile = {
				template: '<div>222</div>'
			};
			const UserPosts = {
				template: '<div>333</div>'
			};
			const UserNull = {
				template: '<div>111</div>'
			}
			//嵌套路由的组要配置是在这里
			//在里边加入childern[]来配置多个嵌套的路由。
			//可以配置一个空，来避免没有参数时的错误。
			const routes = [{
				path: '/user/:id',
				component: User,
				children: [{
						path: '',
						component: UserNull
					},
					{
						path: 'profile',
						component: UserProfile
					},
					{
						path: 'posts',
						component: UserPosts
					}
				]
			}];
			const router = new VueRouter({
				routes
			});

			const app = new Vue({
				el: '#app',
				router
			});
		</script>
	</body>

</html>
