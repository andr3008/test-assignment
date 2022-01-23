<template>
	<v-row class="d-flex">
		<v-col cols="12" md="4">
			<v-text-field
				:readonly="!this.editable"
				v-model="person.first_name"
				label="First name"
			></v-text-field>
		</v-col>

		<v-col cols="12" md="4">
			<v-text-field
				:readonly="!this.editable"
				v-model="person.last_name"
				label="Last name"
			></v-text-field>
		</v-col>
		<v-col cols="12" md="4">
			<v-text-field
				:readonly="!this.editable"
				v-model="person.email"
				label="Email"
			></v-text-field>
		</v-col>
		<v-col cols="12" md="4">
			<v-text-field
				:readonly="!this.editable"
				v-model="person.gender"
				label="Gender"
			></v-text-field> </v-col
		><v-col cols="12" md="4">
			<v-text-field
				:readonly="!this.editable"
				v-model="person.phone"
				label="Phone"
			></v-text-field>
		</v-col>
		<v-col cols="12" md="4">
			<v-text-field
				:readonly="!this.editable"
				v-model="person.language"
				label="Language"
			></v-text-field> </v-col
		><v-col cols="12" md="4">
			<v-text-field
				:readonly="!this.editable"
				v-model="person.city"
				label="City"
			></v-text-field>
		</v-col>
	</v-row>
</template>

<script>
export default {
	data: () => ({}),
	props: ["person", "editable"],
};
</script>
