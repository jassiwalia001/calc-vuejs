<template>
  <div class="calc">
    <div class="container max-w-800px mx-auto py-6">
      <!-- Output Box -->
      <div class="border border-gray-custom-300 rounded-lg p-3">
        <div class="relative flex flex-col items-end">
          <svg
            focusable="false"
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            class="w-5 text-gray-500 fill-current absolute top-0 left-0"
          >
            <path
              d="M13 3a9 9 0 0 0-9 9H1l3.89 3.89.07.14L9 12H6c0-3.87 3.13-7 7-7s7 3.13 7 7-3.13 7-7 7c-1.93 0-3.68-.79-4.94-2.06l-1.42 1.42A8.954 8.954 0 0 0 13 21a9 9 0 0 0 0-18zm-1 5v5l4.28 2.54.72-1.21-3.5-2.08V8H12z"
            ></path>
          </svg>

          <div class="text-xs text-gray-500 mb-1">
            <span v-show="calcResult.length > 0">
              {{ calcString2 }} = {{ calcResult }}</span
            >
          </div>
          <div class="text-3xl">
            <span>{{ calcString }}</span>
          </div>
        </div>
      </div>
      <!-- Numpad -->
      <div class="mt-2 -mx-1">
        <table class="w-full table-fixed">
          <tr>
            <td colspan="2">
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center flex items-center justify-around"
              >
                Rad
                <div class="border border-gray-custom-400 h-5"></div>
                Deg
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                x!
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                (
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                )
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                %
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
                @click="clearInput()"
              >
                CE
              </button>
            </td>
          </tr>
          <tr>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                Inv
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                sin
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                ln
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(7)"
              >
                7
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(8)"
              >
                8
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(9)"
              >
                9
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center text-lg"
                @click="input('÷')"
              >
                ÷
              </button>
            </td>
          </tr>
          <tr>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                π
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                cos
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                log
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(4)"
              >
                4
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(5)"
              >
                5
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(6)"
              >
                6
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center text-lg"
                @click="input('x')"
              >
                x
              </button>
            </td>
          </tr>
          <tr>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                e
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                tan
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                √
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(1)"
              >
                1
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(2)"
              >
                2
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(3)"
              >
                3
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center text-lg"
                @click="input('-')"
              >
                -
              </button>
            </td>
          </tr>
          <tr>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                Ans
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                EXP
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center"
              >
                x<sup>y</sup>
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center"
                @click="input(0)"
              >
                0
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-100 h-10 w-full text-center font-bold"
                @click="inputDecimal('.')"
              >
                .
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-blue-custom-100 text-white h-10 w-full text-center text-lg"
                @click="submit()"
              >
                =
              </button>
            </td>
            <td>
              <button
                class="rounded-md bg-gray-custom-200 h-10 w-full text-center text-lg"
                @click="input('+')"
              >
                +
              </button>
            </td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import { evaluate } from "mathjs";

export default {
  name: "Calculator",
  data() {
    return {
      outputNum: "",
      calcString: "0",
      calcString2: "",
      calcResult: "",
      operationSet: false,
      submitDone: false,
    };
  },
  methods: {
    input(num) {
      if (this.calcString === "0" || this.submitDone) {
        this.calcString = num;
        this.submitDone = false;
      } else {
        this.calcString = `${this.calcString}${num}`;
      }
    },
    inputDecimal(decimal) {
      let inputNumbers = this.calcString
        .toString()
        .split("x")
        .join(", ")
        .split("+")
        .join(", ")
        .split("÷")
        .join(", ")
        .split("-")
        .join(", ");

      inputNumbers = inputNumbers.split(",");

      if (inputNumbers[inputNumbers.length - 1].indexOf(decimal) > -1) return;

      this.calcString = this.calcString + decimal;
    },
    clearInput() {
      this.submitDone = false;
      this.calcString = "0";
    },
    submit() {
      let evalString = this.calcString.replace(/x/g, "*").replace(/÷/g, "/");
      this.submitDone = true;
      this.calcString2 = this.calcString;
      this.calcResult = evaluate(evalString).toString();
      this.calcString = evaluate(evalString).toString();
      if (this.calcString === this.calcString2) {
        this.calcString2 = "Ans";
      }
    },
  },
};
</script>

<style scoped>
table td {
  @apply p-1;
}
</style>
