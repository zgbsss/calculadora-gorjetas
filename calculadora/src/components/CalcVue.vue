<script>
export default {
  data() {
    return {
      qualidades: [
        { qualidade: 5, servico: "5% (Horrivel)" },
        { qualidade: 10, servico: "10% (Ruim)" },
        { qualidade: 15, servico: "15% (Ok)" },
        { qualidade: 20, servico: "20% (Bom)" },
        { qualidade: 25, servico: "25% (Ótimo)" },
        { qualidade: 30, servico: "30% (Excepcional)" },
      ],
      valor: 0,
      pessoa: 1,
      qual_selecionada: "",
    };
  },
  computed: {
    final_v() {
      return (
        (this.valor * (1 + this.qual_selecionada / 100)) /
        this.pessoa
      ).toFixed(2);
    },
  },
};
</script>
<template>
  <main>
    <div class="calc">
      <h1>Calculadora de <strong>Gorjetas</strong></h1>
      <div class="valores-forms">
        <label for="input-valor">Insira o valor da conta:</label>
        <input v-model="valor" placeholder="0" id="input-valor" type="number" />
      </div>
      <div class="valores-forms">
        <label for="select-servico">Qual foi a qualidade do serviço?</label>
        <select
          v-model="qual_selecionada"
          name="select-qualidade"
          id="select-servico"
        >
          <option disabled value="">Escolha um item</option>
          <option
            v-for="qualidade of qualidades"
            :key="qualidade.qualidade"
            for="select-servico"
            :value="qualidade.qualidade"
          >
            {{ qualidade.servico }}
          </option>
        </select>
      </div>
      <div class="valores-forms">
        <label for="input-pessoas">Insira quantas pessoas vão pagar a conta:</label>
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
      <span>R$ {{ final_v }} por pessoa</span>
    </div>
  </main>
</template>
