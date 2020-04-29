<template>
<!--  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div> -->
  <div class="page">
	<img alt="Vue logo" src="./assets/logo.png">
    <div id="map" class="map" ref="map" style="width: 1000px;height: 1000px;">
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

// export default {
//   name: 'app',
//   components: {
//     HelloWorld
//   }
// }

import RelationChart from 'relation-chart'
import alipay from './assets/alipay.png'
import weixin from './assets/weixin.png'
import vue from './assets/logo.png'
import yijia from './assets/yijia.png'
import dazhong from './assets/dazhong.png'
import mayi from './assets/mayi.png'
import tencent from './assets/tencent.png'
import apple from './assets/apple.png'
import citibank from './assets/citibank.png'
export default {
  data () {
    return {
		data:{
			nodes: [
				{
					"name": "蚂蚁金服",
					"role_id": 41,
					 "group": 1,
					"avatar": mayi
				},
				{
					"name": "腾讯",
					"role_id": 42,
					"avatar": tencent
				},
				{
					"name": "苹果",
					"role_id": 43,
					"avatar": apple
				},
				{
					"name": "宜家",
					"role_id": 44,
					"avatar": yijia
				},
				{
					"name": "大众",
					"role_id": 45,
					"avatar": dazhong
				},
				{
					"name": "花旗银行",
					"role_id": 46,
					"avatar": citibank
				},
			],
			links: [
				{
					"source": 0,
					"target": 1,
					"relation": "付款",
					"color": "734646"
				},
				{
					"source": 0,
					"target": 2,
					"relation": "付款",
					"color": "734646"
				},
				{
					"source": 3,
					"target": 0,
					"relation": "收款",
					"color": "734646"
				},
				{
					"source": 4,
					"target": 0,
					"relation": "收款",
					"color": "734646"
				},
				{
					"source": 4,
					"target": 3,
					"relation": "付款",
					"color": "734646"
				},
				{
					"source": 2,
					"target": 5,
					"relation": "付款",
					"color": "734646"
				},
			],
		}
	}
  },
  mounted() {
    this.rchart()
  },
  methods:{
	rchart:function(){
		const rc = new RelationChart(this.$refs.map, this.data)
		rc.circles.on('click', function (d) {
		    console.log('头像节点click1')
		})
		rc.texts.on('click', function (d) {
			console.log('关系文本 click')
		})
		rc.edges.on('click', function (d) {
			console.log('线click')
		})
	}
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
