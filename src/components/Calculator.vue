<template>
  <div class="title">
    <h1>{{ msg }}</h1>
  </div>
  <section class="calculator">
    <div class="displayResult">
      {{ calculatorValue || 0 }}
    </div>

    <!-- Calculator buttons -->
    <div class="calculator__input">
      <button
        @click="action(n)"
        v-for="n in calculatorElements"
        :key="n"
        :class="{
          calculator__button: ['C', '*', '/', '-', '+', '%', '='].includes(n),
        }"
      >
        {{ n }}
      </button>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    msg: String,
  },
  data() {
    return {
      calculatorValue: "",
      calculatorElements: [
        "C",
        "*",
        "/",
        "-",
        7,
        8,
        9,
        "+",
        4,
        5,
        6,
        "%",
        1,
        2,
        3,
        "=",
        0,
        ".",
      ],
      operator: null,
      previousCalculatorValue: "",
    };
  },
  methods: {
    action(n) {
      /* Append value */
      if (!isNaN(n) || n === ".") {
        this.calculatorValue += n + "";
      }
      /* Clear value */
      if (n === "C") {
        this.calculatorValue = "";
      }
      /* Percentage */
      if (n === "%") {
        this.calculatorValue = this.calculatorValue / 100 + "";
      }
      /* Operators */
      if (["/", "*", "-", "+"].includes(n)) {
        this.operator = n;
        this.previousCalculatorValue = this.calculatorValue;
        this.calculatorValue = "";
      }
      /* Calculate result using the eval function */
      if (n === "=") {
        this.calculatorValue = eval(
          this.previousCalculatorValue + this.operator + this.calculatorValue
        );
        this.previousCalculatorValue = "";
        this.operator = null;
      }
    },
  },
};
</script>

<style scoped>
.title {
  text-align: center;
}
.calculator {
  position: relative;
  margin: 5px auto;
  display: flex;
  flex-flow: column nowrap;
  width: 30em;
  height: 35em;
  border: 2px solid papayawhip;
  background: black;
  color: aliceblue;
  border-radius: 5px;
  padding: 1em;
  background: hsl(60, 2%, 12%);
  color: rgb(16, 15, 15);
  font-family: "Courier New";
}
.displayResult {
  font-size: 3em;
  width: 90%;
  min-height: 2em;
  border: 2px solid blueviolet;
  border-radius: 5px;
  padding: 22px;
  margin-bottom: 1em;
  overflow: scroll;
  text-align: right;
  background: black;
  color: aliceblue;
  /* text-overflow: ellipsis; */
  white-space: nowrap;
}
.calculator__input {
  margin: 5px auto;
  padding: 5px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  width: 90%;
  height: 70%;
  justify-content: space-between;
  align-items: center;
  gap: 5px;
  background: rgb(59, 59, 57);
}

.calculator__button {
  display: flex;
  height: 100%;
  width: auto;
  flex-flow: column nowrap;
  column-gap: 0.5em;
  row-gap: 0.5em;
  align-items: center;
  justify-content: center;
  background: orange;
  color: aliceblue;
}
</style>
