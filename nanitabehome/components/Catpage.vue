<script>
import jsondataList from '@/assets/json/jsondata.json'

export default {

	data () {
		return {
			jsondataList: jsondataList,
		}
	},

	created () {

		this.recipeList.forEach((e) => {
			let jpList = this.jsondataList.find(j => j.strMeal === e.strMeal);
			e.strMeal = jpList.strMealjp
		})

	},
 


	props: {
		recipeList: Object,
	},

	methods: {
		clickUrl(recipeUrl) {
			window.open(recipeUrl, '_blank')
		},

		aaa() {
			// this.recipeList.forEach((e) => {
			// 	let jpList = this.jsondataList.find(j => j.strMeal === e.strMeal);
			// 	e.strMeal = jpList.strMealjp
			// })

		}
	}

}
</script>
<template>
<div class="wrap">
	<slot></slot>
	<div class="box aricle_box" v-for="item in recipeList" :key="recipeList"  @click="clickUrl(item.recipeUrl)">
			<div class="media-left">
				<figure class="image is-64x64">
					<img :src="item.strMealThumb" alt="レシピの写真">
				</figure>
			</div>
			<div class="media-content">
				<div class="content">
					<p>
					{{ item.strMeal }}
					</p>
				</div>
			</div>
	</div>
				<button @click="aaa()" >aaa</button>

</div>
</template>
<style lang="scss">
h2 {
	text-align: center;
	margin-bottom: 15px;
}

.aricle_box {
	display: flex;
    cursor: pointer;
    width: 550px;
		
	.media-content {
		margin-left: 20px;
		display: flex;
		align-items: center;

		p {
			font-size: 20px;
		}
		
	}

}

@media screen and ( max-width:479px ) {
    .aricle_box {
        width: auto;
    }
}

</style>