<template>
  <div>
    <section class="calc-btns">
      <div class="calc-btn-row">
        <button
          class="calc-btn"
          v-for="valOptions in keys"
          @click="putValue(valOptions)"
        >
          {{ valOptions }}
        </button>
      </div>
      <div class="grid-container">
        <div class="grid-container-num">
          <button
            class="calc-btn-num"
            v-for="(valueNumber, key) in numbers"
            @click="putValue(valueNumber)"
          >
            {{ valueNumber }}
          </button>
        </div>
        <div class="flex-operator">
          <button
            class="calc-btn-operator"
            v-for="(valueOperator, key) in operators"
            key="key"
            @click="putValue(valueOperator)"
          >
            {{ valueOperator }}
          </button>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Keyboard",
  props: {
    valueFromScreen: "",
  },
  data() {
    return {
      numbers: ["7", "8", "9", "4", "5", "6", "1", "2", "3", "0", ".", "="],
      operators: ["+", "-", "X", "/"],
      keys: ["Del", "(", ")", "AC"],
      arrCalc: [],
      checkOn: true,
      result: 0,
    };
  },
  methods: {
    reset() {
      // làm 2 việc vừa đưa mảng về rỗng và kết quả về 0
      this.arrCalc = [];
      this.result = 0;
      this.$emit("resultNumber", this.result);
    },
    putValue(key) {
      // ... : toán tử es6
      const toScreenArr = [...this.numbers, ...this.operators];

      // nếu checkon = false thì out luôn
      if (!this.checkOn) return;
      switch (key) {
        case "AC":
          this.reset();
          break;
        case "Del":
          //nếu mảng ko có giá trị thì out luôn
          if (!this.arrCalc.length) return;
          if (this.arrCalc.length == 1) {
            return this.reset();
          }
          this.arrCalc.pop();
          this.$emit("resultNumber", this.arrCalc);
          break;
        case "=":
          if (!this.arrCalc.length) return;
          let newString = this.arrCalc.toString().replaceAll(",", "");
          if (newString == "()") return this.reset();
          if (this.arrCalc.length == 1 && this.arrCalc[0] == "-") {
            //khi phan tu đầu tiên "-"
            this.reset();
            return;
          }
          try {
            this.result = eval(newString);
            
            // Do something that might trigger an error
          } catch (error) { 
          } finally {
            if (this.result) {
              this.arrCalc = [this.result];
              this.$emit("resultNumber", this.result);
            }
            else{this.reset();}
            // Code here always runs. Doesn't matter if there was an error or not.
          }
          // Only runs when there is an error/exception

          break;

        default:
          if (
            this.numbers.includes(key) ||
            this.operators.includes(key) ||
            ["(", ")"].includes(key)
          ) {
            if (!this.arrCalc.length && key == ")") return;

            // chỉ đc trừ đứng đầu
            if (!this.arrCalc.length && ["+", "/", "X"].includes(key)) return;

            //loại các trường hợp dấu gần kề nhau
            if (
              (this.arrCalc.at(-1) == "-" && this.operators.includes(key)) ||
              (["+", "/", "*"].includes(this.arrCalc.at(-1)) &&
                ["+", "/", "X"].includes(key))
            )
              return;
            // dấu "X" = *
            if (key == "X") key = "*";
            this.arrCalc.push(key);
            this.$emit("arrCalc", this.arrCalc);
          }
      }
      // code block
    },
  },
};
</script>

<style>
.calc-btn-row {
  display: flex;
  justify-content: space-between;
  margin: 5% 0;
  flex-wrap: wrap;
}
.calc-btn {
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(255, 255, 255, 0.01);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  flex-basis: 20%;
  font-family: inherit;
  font-size: 24px;
  height: 65px;
}
.calc-btn-num {
  width: 65px;
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(255, 255, 255, 0.01);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  flex-basis: 30%;
  font-family: inherit;
  font-size: 24px;
  height: 65px;
  align-content: space-between;
}
.calc-btn-operator:hover,
.calc-btn-num:hover {
  background-color: gray;
}
.calc-btn-operator {
  width: 100%;
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(255, 255, 255, 0.01);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  font-family: inherit;
  font-size: 24px;
  height: 65px;
  align-content: center;
}
.calc-btn {
  backdrop-filter: blur(5.5px);
  -webkit-backdrop-filter: blur(5.5px);
  background: rgba(255, 255, 255, 0.75);
  border: 1px solid rgba(255, 255, 255, 0.01);
  border-radius: 16px;
  box-shadow: 0 4px 30px rgba(35, 35, 35, 0.1);
  color: black;
  background: orange;
}
.calc-btn:hover {
  background-color: inherit;
}
.calc-btn:active {
  background-color: gray;
}
.list-operator {
  flex-direction: column;
}
.list-number {
  width: 90%;
}
.flex-operator {
  display: flex;
  height: 100%;
  justify-content: space-between;
  flex-direction: column;
}

.grid-container {
  display: grid;
  grid-template-columns: 80% 20%;
  align-items: center;
}
.grid-container-num {
  display: grid;
  grid-template-columns: auto auto auto;
  grid-gap: 21px;
  align-content: space-around;
  justify-content: center;
  margin-left: -22px;
}
</style>
