<template>
	<v-container fluid fill-height class="green lighten-5">
		<v-row no-gutters>
			<v-card class="mx-auto" width="600" outlined>
				<v-card-title>Search People</v-card-title>
				<v-form class="d-flex flex-row mb-6">
					<v-text-field
						class="ml-8"
						color="grey"
						label="Filter text"
					></v-text-field>

					<v-btn class="mx-8 mt-2 grey--text">Search</v-btn>
				</v-form>
			</v-card>
		</v-row>

		<v-row class="mt-28 mb-12">
			<v-card class="mx-auto" max-width="600" outlined>
				<v-card-title>Search Result</v-card-title>
				<v-data-table
					:headers="dessertHeaders"
					:items="desserts"
					:items-per-page="5"
					class="elevation-1"
				>
				</v-data-table>
			</v-card>
		</v-row>
	</v-container>
</template>

<script>
export default {
	name: "Searchbar",

	methods: {},

	data() {
		return {
			expanded: [],
			singleExpand: false,
			dessertHeaders: [
				{
					text: "Dessert (100g serving)",
					align: "start",
					sortable: false,
					value: "name",
				},
				{ text: "Calories", value: "calories" },
				{ text: "Fat (g)", value: "fat" },
				{ text: "Carbs (g)", value: "carbs" },
				{ text: "Protein (g)", value: "protein" },
				{ text: "Iron (%)", value: "iron" },
				{ text: "", value: "data-table-expand" },
			],
			desserts: [
				{
					name: "Frozen Yogurt",
					calories: 159,
					fat: 6.0,
					carbs: 24,
					protein: 4.0,
					iron: "1%",
				},
				{
					name: "Ice cream sandwich",
					calories: 237,
					fat: 9.0,
					carbs: 37,
					protein: 4.3,
					iron: "1%",
				},
				{
					name: "Eclair",
					calories: 262,
					fat: 16.0,
					carbs: 23,
					protein: 6.0,
					iron: "7%",
				},
				{
					name: "Cupcake",
					calories: 305,
					fat: 3.7,
					carbs: 67,
					protein: 4.3,
					iron: "8%",
				},
				{
					name: "Gingerbread",
					calories: 356,
					fat: 16.0,
					carbs: 49,
					protein: 3.9,
					iron: "16%",
				},
				{
					name: "Jelly bean",
					calories: 375,
					fat: 0.0,
					carbs: 94,
					protein: 0.0,
					iron: "0%",
				},
				{
					name: "Lollipop",
					calories: 392,
					fat: 0.2,
					carbs: 98,
					protein: 0,
					iron: "2%",
				},
				{
					name: "Honeycomb",
					calories: 408,
					fat: 3.2,
					carbs: 87,
					protein: 6.5,
					iron: "45%",
				},
				{
					name: "Donut",
					calories: 452,
					fat: 25.0,
					carbs: 51,
					protein: 4.9,
					iron: "22%",
				},
				{
					name: "KitKat",
					calories: 518,
					fat: 26.0,
					carbs: 65,
					protein: 7,
					iron: "6%",
				},
			],
		};
	},
};
</script>
