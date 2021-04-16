<template>
	<div class="income-item">
		<div class="removeItem" @click="deleteItem(income.id)">x</div>
		<div class="desc">{{ income.desc }}</div>
		<div class="price">${{ income.value }}</div>
		<div class="date">{{ formattedDate }}</div>
	</div>
</template>
<script>
export default {
	props: {
		income: Object
	},
	setup(props, { emit }) {
		let date = new Date(props.income.date);
		let day = date.getDate();
		let month = date.getMonth();
		let year = date.getFullYear();

		let formattedDate = day + "/" + month + "/" + year;
    
    function deleteItem(item) {
      emit("delete-item", item)
    }
		return {
      formattedDate,
      deleteItem
    };
	}
};
</script>
<style scoped>
.income-item {
	position: relative;
	display: flex;
	padding: 15px 15px 15px 0;
	background-color: #fff;
	border-radius: 8px;
	max-width: 900px;
	margin: 0 auto 30px;
}
.removeItem {
	color: #ef2d2d;
	font-weight: 600;
	font-size: 20px;
	line-height: 1;
	text-align: center;
	margin: 0 15px;
  cursor: pointer;
}
.desc {
	color: #666;
	flex: 1 1 100%;
	font-size: 20px;
}
.price {
	color: #666;
	min-width: 100px;
	font-size: 20px;
}
.date {
	color: #666;
	font-size: 20px;
	text-align: right;
}
</style>