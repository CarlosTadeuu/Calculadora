<script setup>
import {reactive} from "vue";

const estado = reactive({
	num1: null,
	num2: null,
	operador: "soma",
});

function calcular() {
	switch (estado.operador) {
		case "soma":
			return estado.num1 + estado.num2;
		case "subtração":
			return estado.num1 - estado.num2;
		case "multiplicação":
			return estado.num1 * estado.num2;
		case "divisão":
			return estado.num2 === 0 ? "Divisão por zero" : estado.num1 / estado.num2;
	}
}
</script>

<template>
	<div class="container">
		<div class="row d-flex flex-column align-items-center gap-2">
			<div class="col-4 d-flex flex-column align-items-center gap-2">
				<h1>Qual seu calculo?</h1>
				<div class="d-flex gap-3">
					<input
						placeholder="Digite um numero"
						class="form-control"
						required
						type="number"
						v-model="estado.num1"
					/>
					<input
						class="form-control"
						required
						type="number"
						v-model="estado.num2"
						placeholder="Digite outro numero"
					/>
				</div>
			</div>
			<div class="col-4 gap-2 d-flex flex-column justify-content-center">
				<select
					@change="
						(e) => {
							estado.operador = e.target.value;
						}
					"
					class="form-select"
				>
					<option value="soma">Soma</option>
					<option value="subtração">Subtração</option>
					<option value="multiplicação">Multiplicação</option>
					<option value="divisão">Divisão</option>
				</select>
				<h2>O resultado é: {{ calcular() }}</h2>
			</div>
		</div>
	</div>
</template>

<style scoped></style>
