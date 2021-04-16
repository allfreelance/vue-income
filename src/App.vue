<template>
	<Header :totalIncome="state.totalIncome" />
	<Form @add-income="AddIncome" />
	<IncomeList :state="state" @deleteItem="deleteItem"></IncomeList>
</template>

<script>
import IncomeList from "./components/IncomeList";
import Form from "./components/Form";
import { reactive, computed } from "vue";
import Header from "./components/Header";

export default {
	components: {
		IncomeList,
		Form,
		Header
	},
	setup() {
		const state = reactive({
			income: [],
			totalIncome: computed(() => {
				let temp = 0;
				if (state.income.length > 0) {
					for (let i = 0; i < state.income.length; i++) {
						temp += state.income[i].value;
					}
				}
				return temp;
			})
		});

		function AddIncome(data) {
			let d = data.date.split("-");
			let newD = new Date(d[0], d[1], d[2]);

			state.income = [
				...state.income,
				{
					id: Date.now(),
					desc: data.desc,
					value: parseInt(data.value),
					date: newD.getTime()
				}
			];
		}
    
    function deleteItem(item) {
      state.income.forEach((elem, index) => (elem.id === item) ? state.income.splice(index, 1) : '')
    }
    
		return {
			Header,
			Form,
			state,
			AddIncome,
      deleteItem
		};
	}
};
</script>

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
body {
	background-color: #eee;
}
</style>
