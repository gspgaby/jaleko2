<template>
	<div>	
		<label>Encontre o seu video!</label>
		<input @keyup.enter="onInput" placeholder="Pesquisar" />
	</div>
</template>

<script>
export default {
	name: 'SearchBar',
	methods: {
		onInput: function(e) {
			this.$emit('searchTermChange', e.target.value);
		}
	}
};
</script>

<style scoped>
	label{
		display: block;
		font-size: 19px;
		margin-bottom: 0.5%;
	}
	
	input {
		
		width: 30%;
		border-radius: 8px;
		border: 1px solid #6a7bb4;
		padding: 12px;
		outline: none;
		
	}
	div {
		text-align: center;
		margin: 10%;
	}
	input::placeholder{
		align-items: center;
	}
</style>