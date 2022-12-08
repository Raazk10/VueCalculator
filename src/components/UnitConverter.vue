<template>
  <section class="unit-converter">
    <div v-for="weight in weightConverter" :key="weight">
      <label {{weight.id}}></label>
      <input
        @input="weightConverter(weight.id)"
        class="unit-converter__input"
        type="number"
        :placeholder="Pounds"
        v-model="weight.input"
      />
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      weightConvert: [
        {
          id: "pound",
          input: 0,
        },
        {
          id: "kilogram",
          input: 0,
        },
        {
          id: "ounces",
          input: 0,
        },
        {
          id: "gram",
          input: 0,
        },
      ],
    };
  },

  computed: {},

  methods: {
    weightConverter(source) {
      let convert = this
        pound = convert.weightConvert[0],
        kilogram = convert.weightConvert[1];
		    ounce = convert.weightConvert[2],
	  	  gram = convert.weightConvert[3]

		  if(source=pound){
			kilogram.input =
		  }
    },

    handleInputChange() {
      this.output = this.returnMetersByMetric(
        this.inputInMeters,
        this.selectedOutputMetric
      );
    },

    handleOutputChange() {
      this.input = this.returnMetersByMetric(
        this.outputInMeters,
        this.selectedInputMetric
      );
    },
  },
};
</script>

<style>
.unit-converter {
  border: 2px solid lightgray;
  padding: 5rem;
  font-size: 2em;
  margin-bottom: 1em;
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-around;
}

.unit-converter__input {
  border: 2px solid lightgray;
}
</style>
