<template>
	<div class="ClassifyPage">
		<!--菜单-->
		<div class="menuBox" v-show="bool">
			<div class="sanjiao"></div>
			<div class="powers">
				<div class="toHome" @click="comeIndex">
					<span class="bgH"></span>
					<span class="fontsH">首页</span>
				</div>
				<div class="toClassify" @click="comeClass">
					<span class="bgCl"></span>
					<span class="fontCl">分类</span>
				</div>
				<div class="toCar" @click="comeCart">
					<span class="bgCa"></span>
					<span class="fontCa">购物车</span>
				</div>
				<div class="toMine"  @click="comeMy">
					<span class="bgM"></span>
					<span class="fontM">我的</span>
				</div>
			</div>
		</div>
		<!--头部-->
		<div class="header">
			<div class="back" @click="backFn"></div>
			<div class="pgTitle">{{ pgTitle }}</div>
			<div class="menu" @click="menuFn"></div>
		</div>
		<!--分类内容-->
		<div class="ClaMain">
			<div class="ClaMain_left">
				<div class="theSame" v-for="(theme,indexA) in themes" @click="change(indexA)" :class="{bg: i==indexA}">{{ theme }}</div>
			</div>
			<div class="ClaMain_right">
				<div class="firstShow">
					<router-link :to="{path:'/details',query:{teaTitle:val,teaLists:teaType}}">
						<div class="firstShow_T" >进入{{val}}频道  ></div>
					</router-link>
					<div class="list" v-for="tea in teaType" @click="toDetails">{{tea}}</div>
				</div>
			</div>
		</div>
		<navigator></navigator>
	</div>
</template>

<script>
    import Navigator from '../common/Navigator'

    export default {
        data() {
            return {
                pgTitle:"全部分类",
                themes:["花茶","六大茶山","大益普洱茶","中茶","瑜山日照绿","风牌红茶","金灶"],
                i:0,
                val:"花茶",
                teaType:["花草茶","中药调饮"],
                bool:false,
            }
        },
		components: {
            Navigator
		},
        methods:{
            change:function(ind){
                this.i = ind;
                switch (ind){
                    case 0:
                        this.val = "花茶";
                        this.teaType=["花草茶","中药调饮"];
                        break;
                    case 1:
                        this.val = "六大茶山";
                        this.teaType=["贺开庄园系列","俊昌号系列","六大茶山系列","鼎立滇红"];
                        break;
                    case 2:
                        this.val = "大益普洱茶";
                        this.teaType=["大益普洱茶"];
                        break;
                    case 3:
                        this.val = "中茶";
                        this.teaType=["中茶普洱茶","黑茶"];
                        break;
                    case 4:
                        this.val = "瑜山日照茶";
                        this.teaType=["日照绿茶"];
                        break;
                    case 5:
                        this.val = "风牌红茶";
                        this.teaType=["风牌红茶","普洱茶"];
                        break;
                    case 6:
                        this.val = "金灶";
                        this.teaType=["电热茶炉","玻璃茶具","成套茶具"];
                        break;
                }
            },
            toDetails:function(){
                this.$router.push("/details")
            },
            menuFn:function(){
                this.bool = !this.bool;
            },
            backFn:function(){
                this.$router.push({path: history.go(-1)})
            },
            comeIndex(){
                this.$router.push("/")
            },
            comeClass(){
                this.$router.push("/classify")
            },
            comeCart(){
                this.$router.push("/car")
            },
            comeMy(){
                this.$router.push("/mine")
            }
        },
        mounted: function () {

        }
    }
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
	.bg
		border-left 0.0666rem solid #e71f19
		color: #e71f19
		background-color #f5f5f5
	.ClassifyPage
		width 100%
		position fixed
		left 0
		top 0
		/*菜单*/
		.menuBox
			position absolute
			right 0
			top 1.2rem
			background-color rgba(0,0,0,0.8)
			width 25%
			z-index 10
			.sanjiao
				position absolute
				right 14%
				top -0.3333rem
				width 0
				height 0
				border-left 0.2666rem solid transparent
				border-right 0.2666rem solid transparent
				border-bottom 0.3333rem solid rgba(0,0,0,0.8)
			.powers
				color lightgray
				.toHome
					position relative
					padding 0.1666rem 0.1333rem
					border-bottom 1px solid lightgray
					.bgH
						position absolute
						left 5%
						top 0.1666rem
						display inline-block
						width 0.7rem
						height 0.7rem
						background url('/static/img/ClassifyPage/homes.png') no-repeat
						background-position center center
						background-size 90%
					.fontsH
						font-size 0.4rem
						display inline-block
						margin-left 0.85rem
						margin-bottom:0.2rem
						margin-top:0.1666rem
				.toClassify
					position relative
					padding 0.1666rem 0.1333rem
					border-bottom 1px solid lightgray
					.bgCl
						display inline-block
						width 0.7rem
						height 0.7rem
						background url('/static/img/ClassifyPage/classify.png') no-repeat
						background-position center center
						background-size 120%
					.fontCl
						position absolute
						left 0
						top 0.3rem
						font-size 0.4rem
						display inline-block
						margin-left 1rem
				.toCar
					position relative
					padding 0.1666rem 0.1333rem
					border-bottom 1px solid lightgray
					.bgCa
						display inline-block
						width 0.7rem
						height 0.7rem
						background url('/static/img/ClassifyPage/shopCar.png') no-repeat
						background-position center center
						background-size 90%
					.fontCa
						position absolute
						left 0
						top 0.3rem
						font-size 0.4rem
						display inline-block
						margin-left 1rem
				.toMine
					position relative
					padding 0.1666rem 0.1333rem
					border-bottom 1px solid lightgray
					.bgM
						display inline-block
						width 0.7rem
						height 0.7rem
						background url('/static/img/ClassifyPage/my.png') no-repeat
						background-position center center
						background-size 90%
					.fontM
						position absolute
						left 0
						top 0.3rem
						font-size 0.4rem
						display inline-block
						margin-left 1rem
		/*头部*/
		.header
			height 1.2rem
			line-height 1.2rem
			/*background-color red*/
			text-align center
			position relative
			left 0
			top 0
			.back
				position absolute
				left 0
				top 0
				width 1.2rem
				height 1.2rem
				background url('/static/img/ClassifyPage/back.png') no-repeat
				background-position center center
				background-size 50%
			.pgTitle
				font-size 0.5066rem
				color #333333
			.menu
				position absolute
				right 0
				top 0
				width 1.2rem
				height 1.2rem
				background url('/static/img/ClassifyPage/menu.png') no-repeat
				background-position center center
				background-size 100%
		/*分类内容*/
		.ClaMain
			position relative
			left 0
			top 0
			background-color #f5f5f5
			.ClaMain_left
				position absolute
				left 0
				top 0
				width 25%
				height: 22.6666rem
				/*border 1px solid red*/
				text-align center
				.theSame
					border-top 0.0333rem solid #f5f5f5
					border-bottom 0.0333rem solid #f5f5f5
					font-size 0.45rem
					padding 0.4666rem 0
			.ClaMain_right
				position absolute
				right 0
				top 0
				width 75%
				height: 22.6666rem
				/*border 1px solid aqua*/
				background-color #f5f5f5
				.msg
					width 90%
					height 0.9333rem
					line-height 0.9333rem
					text-align center
					background-color #e71f19
					border-radius 0.1333rem
					margin 3.5% auto
					font-size 0.4rem
					color #fff
				.firstShow
					position absolute
					right 0
					top 0
					width 100%
					height: 22.6666rem
					/*border 1px solid aqua*/
					background-color #f5f5f5
					.firstShow_T
						width 90%
						height 0.9333rem
						line-height 0.9333rem
						text-align center
						background-color #e71f19
						border-radius 0.1333rem
						margin 4% auto
						font-size 0.4rem
						color #fff
					.list
						/*border 1px solid red*/
						color gray
						width 90%
						margin 0 auto
						margin-bottom 0.3333rem
						font-size 0.4rem
</style>