<template>
	<div class="box">
		<div>
			<ul>
				<li class="head_p">
					<div><img src="/static/minePage/1.png"/></div>
				</li>
				<li class="login">
					<router-link to="/login" v-show="!exits">登录</router-link>
					<a v-show="exits" >{{successName}}</a>
				</li>
				<li class="list">
					<span>收藏</span>
					<span>消息</span>
					<span>可用积分</span>
				</li>
			</ul>
			<div class="order">
				<router-link to="/orderList">
					全部订单
					<img src="/static/minePage/11.png" alt="" />
				</router-link>
			</div>
			<ul class="nav">
				<li v-for="i in arr"><router-link :to="i.path">{{i.title}}</router-link></li>
			</ul>
			<ul class="ipt">
				<li>
					<span v-for="item in arr1">
						{{item.name}}
						<img :src="item.src" alt="" />
					</span>
				</li>
			</ul>
		</div>
		<navigator></navigator>
	</div>
</template>

<script>
    import Navigator from '../common/Navigator'
    import Login from './Login'

    export default {
        data:function(){
            return {
                arr:[
                    { 'title': '待付款', 'path': '/payAwait'},
                    { 'title': '待发货', 'path': '/sendAwait'},
                    { 'title': '待收货', 'path': '/takeAwait'},
                    { 'title': '待评价', 'path': '/evaluateAwait'}
				],
                arr1:[{'name':'我的购物车','src':require('../../../static/minePage/11.png')},
                    {'name':'我的会员','src':require('../../../static/minePage/11.png')},
                    {'name':'客服热线','src':require('../../../static/minePage/11.png')},
                    {'name':'我的上传','src':require('../../../static/minePage/11.png')},
                    {'name':'我的设置','src':require('../../../static/minePage/11.png')}],
                arr2:[{'path':'/mine/login'}],
                successName: ""
            }
        },
        methods:{
            loginFn:function(){
                console.log(1);
            },

//            updateCookie:function(){
//                console.log(this.getCookie("username"));
//                console.log(this.getCookie("pwd"));
//                var username = this.getCookie("username");
//                var pwd = this.getCookie("pwd");
//                if(username == this.userName&& pwd == this.pwd){
//                    alert("登录成功");
//                    this.userName="";
//                    this.pwd="";
//                    this.$router.push("/mine");
//                }else{
//                    alert("账号或者密码错误,请重新输入")
//                }
//            },
//            getCookie:function(cname){
//                var name = cname + "=";
//                var ca = document.cookie.split(';');
//                for (var i = 0; i < ca.length; i++) {
//                    var c = ca[i];
//                    while (c.charAt(0) == ' ') c = c.substring(1);
//                    if (c.indexOf(name) != -1) return c.substring(name.length, c.length);
//                }
//                return "";
//            },
//			gogo(){
//                this.$store.commit('gogo')
//			}
        },
        components:{
            Navigator,
            Login
        },
		mounted(){
//            updateCookie:function(){
//                console.log(this.getCookie("username"));
//                console.log(this.getCookie("pwd"));
//                var username = this.getCookie("username");
//                var pwd = this.getCookie("pwd");
//                if(username == this.userName&& pwd == this.pwd){
//                    alert("登录成功");
//                    this.userName="";
//                    this.pwd="";
//                    this.$router.push("/mine");
//                }else{
//                    alert("账号或者密码错误,请重新输入")
//                }
//            },
            function getCookie(cname){
                var name = cname + "=";
                var ca = document.cookie.split(';');
                for (var i = 0; i < ca.length; i++) {
                    var c = ca[i];
                    while (c.charAt(0) == ' ') c = c.substring(1);
                    if (c.indexOf(name) != -1) return c.substring(name.length, c.length);
                }
                return "";
            };
            console.log(getCookie("username"));
            console.log(getCookie("pwd"));
            var username = getCookie("username");
            var pwd = getCookie("pwd");
//            if(username == this.userName&& pwd == this.pwd){
//                alert("登录成功");
//                this.userName="";
//                this.pwd="";
//                this.$router.push("/mine");
//            }else{
//                alert("账号或者密码错误,请重新输入")
//            }
			this.successName = username;
		},
			computed:{
		    	exits(){
		    	    return this.$store.state.exits
				}
			}
    }
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
	.head_p
		text-align center
		margin 1rem 0 0.5rem
		div
			display inline-block
			width 3rem
			img
				width 100%
	.order
		padding 0.3rem 0.4rem
		position relative
		background-color #fff
		border-bottom 1px solid #c5c4c4
		span
			color #424242
			display block
			font-size 0.4rem
			img
				position absolute
				right 0.5rem
				top 0.4rem
	.login
		text-align center
		margin-bottom 0.5rem
		a
			display inline-block
			padding 0.2rem 0.4rem
			border 3px solid #c3ad88
			font-size 0.5rem
			color #c3ad88
			background-color #fff
			border-radius 18px
	.list
		padding 0 0.2rem
		display flex
		position relative
		span
			flex 1
			font-size 0.4rem
			display block
			width 10rem
			border-top 2px solid #c5c4c4
			border-bottom 2px solid #c5c4c4
			padding 0.3rem 0.2rem
			color #939393
			text-align center
		span:nth-child(2)
			border 2px solid #c5c4c4
	.nav
		display flex
		background-color #fff
		padding 0.3rem 0
		border-bottom 1px solid #c5c4c4
		li
			flex 1
			text-align center
			a
				display block
				font-size 0.3rem
				color #a6a6a6
				padding-top 0.8rem

		li:nth-child(1)
			a
				background url('../../../static/minePage/2.png') 50% -0.1rem no-repeat
				background-size 1rem
		li:nth-child(2)
			a
				background url('../../../static/minePage/3.png') 50% -0.1rem no-repeat
				background-size 1rem
		li:nth-child(3)
			a
				background url('../../../static/minePage/4.png') 50% -0.2rem no-repeat
				background-size 1rem
		li:nth-child(4)
			a
				background url('../../../static/minePage/5.png') 50% -0.1rem no-repeat
				background-size 1rem
	.ipt
		background-color #fff
		li
			span
				padding 0.3rem 0.4rem
				color #424242
				display block
				font-size 0.3rem
				position relative
				border-bottom 1px solid #c5c4c4
				img
					position absolute
					right 0.5rem
					top 0.35rem
	.info
		width 100%
		height 100%
		position absolute
		left 0
		top 0
		z-index 10
		display none
		.show
			display block
</style>
