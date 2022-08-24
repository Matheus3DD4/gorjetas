<script>
export default {
  data() {
    return {
      qualities: [
        { quality: 5, servico: "5% (Péssimo)" },
        { quality: 10, servico: "10% (Ruim)" },
        { quality: 15, servico: "15% (OK)" },
        { quality: 20, servico: "20% (Bom)" },
        { quality: 25, servico: "25% (Mais que bom)" },
        { quality: 30, servico: "30% (Excepcional)" },
      ],
      value: 0,
      pessoa: 1,
      quality_select: "",
    };
  },
  computed: {
    value_final() {
      return (
        (this.value * (1 + this.quality_select / 100)) /
        this.pessoa
      ).toFixed(2);
    },
  },
};
</script>
<template>
  <main>
    <div class="calc">
      <h1>Calculadora de Gorjetas</h1>
      <div class="values-forms">
        <label for="input-value">Qual o valor da conta?</label>
        <input v-model="value" placeholder="0" id="input-value" type="number" />
      </div>
      <div class="values-forms">
        <label for="select-servico">Como foi o serviço?</label>
        <select
          v-model="quality_select"
          name="select-quality"
          id="select-servico"
        >
          <option disabled value="">Escolha um item</option>
          <option
            v-for="quality of qualities"
            :key="quality.quality"
            for="select-servico"
            :value="quality.quality"
          >
            {{ quality.servico }}
          </option>
        </select>
      </div>
      <div class="values-forms">
        <label for="input-pessoas"
          >Quantas pessoas estão pagando a conta?</label
        >
        <input
          v-model="pessoa"
          placeholder="1"
          id="input-pessoas"
          type="number"
        />
      </div>
    </div>
    <div class="resultado">
      <h2>Valor da conta:</h2>
      <span>R$ {{ value_final }} por pessoa</span>
    </div>
  </main>
</template>
