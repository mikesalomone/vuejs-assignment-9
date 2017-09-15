<template>
	<div>
		<div class="form-group">
	        <label for="firstName">First Name</label>
	        <input 
	                type="text"
	                id="firstName"
	                class="form-control"
	                :value="firstName"
	                @input="emitFullName">
	    </div>
	    <div class="form-group">
	        <label for="lastName">Last Name</label>
	        <input 
	                type="text"
	                id="lastName"
	                class="form-control"
	                :value="lastName"
	                @input="emitFullName">
	    </div>
    </div>
</template>

<script>
	export default {
		props: ['value'],
		methods: {
			emitFullName(event) {
				let name = '';
				if (event.target.id == 'firstName') {
					name = event.target.value + ' ' + this.lastName;
				} else {
					name = this.firstName + ' ' + event.target.value;
				}
				this.$emit('input', name);
			}
		},
		computed: {
			firstName() {
				return this.value.split(" ")[0];
			},
			lastName() {
				return this.value.split(" ")[1];
			}
		}
	}
</script>

<style>

</style>