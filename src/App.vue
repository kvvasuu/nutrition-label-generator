<template>
  <div class="row">
    <!--------------FORM------------>
    <div class="column" id="form-column">
      <div class="form">
        <form id="label-form">
          <!--Serving information-->
          <div class="row">
            <div class="form-group column">
              <label id="servings-label" for="servings"
                >Servings per Container:</label
              >
              <input
                @input="servings = formatToNumbers($event.target.value)"
                type="text"
                name="servings"
                id="servings"
                class="form-control"
                placeholder="Example: 8"
                maxlength="3"
              />
            </div>
            <div class="form-group column">
              <label id="size-label" for="size">Serving Size Quantity:</label>
              <input
                @input="size = $event.target.value"
                type="text"
                name="size"
                id="size"
                class="form-control"
                placeholder="Example: 'cup', 'bottle' etc."
                maxlength="11"
              />
            </div>
          </div>
          <div class="row">
            <div class="form-group column">
              <label id="weight-label" for="weight">Serving size Weight:</label>
              <input
                @input="weight = formatToNumbers($event.target.value)"
                type="text"
                name="weight"
                id="weight"
                class="form-control"
                placeholder="Example: 55"
                maxlength="5"
              />
            </div>
            <div class="form-group column">
              <label id="unit-label" for="unit">Unit:</label>
              <select
                @input="unit = $event.target.value"
                name="unit"
                id="unit"
                class="form-control"
              >
                <option value="g">Grams (g)</option>
                <option value="ml">Mililiters (ml)</option>
              </select>
            </div>
          </div>
          <div class="divider"></div>
          <!--Calories-->
          <div class="form-group">
            <label id="calories-label" for="calories">Calories:</label>
            <input
              @input="calories = formatToNumbers($event.target.value)"
              type="text"
              name="calories"
              id="calories"
              class="form-control"
              maxlength="5"
            />
          </div>
          <div class="divider"></div>
          <!--Fat-->
          <div class="form-group">
            <label id="fat-label" for="fat">Total fat (g):</label>
            <input
              @input="fat = formatToNumbers($event.target.value)"
              type="text"
              name="fat"
              id="fat"
              class="form-control"
              maxlength="5"
            />
          </div>
          <div class="row">
            <div class="form-group column">
              <label id="satfat-label" for="satfat">Saturated Fat (g):</label>
              <input
                @input="saturatedFat = formatToNumbers($event.target.value)"
                type="text"
                name="satfat"
                id="satfat"
                class="form-control"
                maxlength="5"
              />
            </div>
            <div class="form-group column">
              <label id="transfat-label" for="transfat">Trans Fat (g):</label>
              <input
                @input="transFat = formatToNumbers($event.target.value)"
                type="text"
                name="transfat"
                id="transfat"
                class="form-control"
                maxlength="5"
              />
            </div>
          </div>
          <div class="row">
            <div class="form-group column">
              <label id="chol-label" for="chol">Cholesterol (mg):</label>
              <input
                @input="cholesterol = formatToNumbers($event.target.value)"
                type="text"
                name="chol"
                id="chol"
                class="form-control"
                maxlength="5"
              />
            </div>
            <div class="form-group column">
              <label id="sodium-label" for="sodium">Sodium (mg):</label>
              <input
                @input="sodium = formatToNumbers($event.target.value)"
                type="text"
                name="sodium"
                id="sodium"
                class="form-control"
                maxlength="5"
              />
            </div>
          </div>
          <div class="divider"></div>
          <!--Carbohydrates-->
          <div class="row">
            <div class="form-group column">
              <label id="carbo-label" for="carbo"
                >Total Carbohydrate (g):</label
              >
              <input
                @input="carbohydrate = formatToNumbers($event.target.value)"
                type="text"
                name="carbo"
                id="carbo"
                class="form-control"
                maxlength="5"
              />
            </div>
            <div class="form-group column">
              <label id="fiber-label" for="fiber">Dietary Fiber (g):</label>
              <input
                @input="fiber = formatToNumbers($event.target.value)"
                type="text"
                name="fiber"
                id="fiber"
                class="form-control"
                maxlength="5"
              />
            </div>
          </div>
          <div class="row">
            <div class="form-group column">
              <label id="sugar-label" for="sugar">Total Sugars (g):</label>
              <input
                @input="sugar = formatToNumbers($event.target.value)"
                type="text"
                name="sugar"
                id="sugar"
                class="form-control"
                maxlength="5"
              />
            </div>
            <div class="form-group column">
              <label id="addedsugar-label" for="addedsugar"
                >Added Sugars (g):</label
              >
              <input
                @input="addedSugars = formatToNumbers($event.target.value)"
                type="text"
                name="addedsugar"
                id="addedsugar"
                class="form-control"
                maxlength="3"
              />
            </div>
          </div>
          <div class="divider"></div>
          <!--Protein-->
          <div class="form-group">
            <label id="protein-label" for="protein">Protein (g):</label>
            <input
              @input="protein = formatToNumbers($event.target.value)"
              type="text"
              name="protein"
              id="protein"
              class="form-control"
              maxlength="5"
            />
          </div>
          <div class="divider"></div>
          <!--Vitamins-->

          <p class="include">
            <label
              ><input
                v-model="includeVitamins"
                id="include-checkbox"
                name="include"
                type="checkbox"
                class="input-checkbox"
                checked
              />Include vitamins and minerals</label
            >
          </p>
          <div v-if="includeVitamins" class="vitamins">
            <div class="row">
              <div class="form-group column">
                <label id="vitd-label" for="vitd">Vitamin D (mcg):</label>
                <input
                  @input="vitaminD = formatToNumbers($event.target.value)"
                  type="text"
                  name="vitd"
                  id="vitd"
                  class="form-control"
                  maxlength="5"
                />
              </div>
              <div class="form-group column">
                <label id="calcium-label" for="calcium">Calcium (mg):</label>
                <input
                  @input="calcium = formatToNumbers($event.target.value)"
                  type="text"
                  name="calcium"
                  id="calcium"
                  class="form-control"
                  maxlength="5"
                />
              </div>
            </div>
            <div class="row">
              <div class="form-group column">
                <label id="iron-label" for="iron">Iron (mg):</label>
                <input
                  @input="iron = formatToNumbers($event.target.value)"
                  type="text"
                  name="iron"
                  id="iron"
                  class="form-control"
                  maxlength="5"
                />
              </div>
              <div class="form-group column">
                <label id="potassium-label" for="potassium"
                  >Potassium (mg):</label
                >
                <input
                  @input="potassium = formatToNumbers($event.target.value)"
                  type="text"
                  name="potassium"
                  id="potassium"
                  class="form-control"
                  maxlength="5"
                />
              </div>
            </div>
          </div>
        </form>
      </div>
    </div>

    <!--------------LABEL------------>
    <div class="column" id="label-column">
      <div class="label label-all" id="section-to-print">
        <header>
          <h1 class="bold">Nutrition Facts</h1>
          <div class="divider"></div>
          <p>
            <span
              ><span id="servings-value">{{ servings }}</span> servings per
              container</span
            >
          </p>
          <p class="bold">
            <span>Serving size</span>
            <span
              ><span id="size-value">{{ size }} </span>
              <span>
                (<span id="weight-value">{{ weight }}</span
                ><span id="unit-value">{{ unit }}</span
                >)</span
              ></span
            >
          </p>
        </header>
        <div class="divider large"></div>
        <div class="calories-info">
          <div class="left-container">
            <h2 class="bold small-text">Amount per serving</h2>
            <p>Calories</p>
          </div>
          <span id="calories-value">{{ calories }}</span>
        </div>
        <div class="divider medium"></div>
        <div class="daily-value small-text">
          <p class="bold right no-divider">% Daily Value *</p>
          <div class="divider"></div>
          <p>
            <span
              ><span class="bold">Total Fat </span>
              <span id="fat-value">{{ fat }}</span
              >g</span
            >
            <span class="bold percent" id="fat-percent"
              >{{
                calculatePercentage(fat, percentagesMultipliers["fat-percent"])
              }}%</span
            >
          </p>
          <p class="indent no-divider">
            <span
              >Saturated Fat <span id="satfat-value">{{ saturatedFat }}</span
              ><span>g</span></span
            >
            <span class="bold percent" id="satfat-percent"
              >{{
                calculatePercentage(
                  saturatedFat,
                  percentagesMultipliers["satfat-percent"]
                )
              }}%</span
            >
          </p>
          <div class="divider"></div>
          <p class="indent no-divider">
            <span
              ><i>Trans</i> Fat <span id="transfat-value">{{ transFat }}</span
              >g</span
            >
          </p>
          <div class="divider"></div>
          <p>
            <span
              ><span class="bold">Cholesterol </span>
              <span id="chol-value">{{ cholesterol }}</span
              >mg</span
            >
            <span class="bold percent" id="chol-percent"
              >{{
                calculatePercentage(
                  cholesterol,
                  percentagesMultipliers["chol-percent"]
                )
              }}%</span
            >
          </p>
          <p>
            <span
              ><span class="bold">Sodium </span>
              <span id="sodium-value">{{ sodium }}</span
              >mg</span
            >
            <span class="bold percent" id="sodium-percent"
              >{{
                calculatePercentage(
                  sodium,
                  percentagesMultipliers["sodium-percent"]
                )
              }}%</span
            >
          </p>
          <p>
            <span
              ><span class="bold">Total Carbohydrate </span>
              <span id="carbo-value">{{ carbohydrate }}</span
              >g</span
            >
            <span class="bold percent" id="carbo-percent"
              >{{
                calculatePercentage(
                  carbohydrate,
                  percentagesMultipliers["carbo-percent"]
                )
              }}%</span
            >
          </p>
          <p class="indent no-divider">
            <span
              >Dietary Fiber <span id="fiber-value">{{ fiber }}</span
              >g</span
            >
          </p>
          <div class="divider"></div>
          <p class="indent no-divider">
            <span
              >Total Sugars <span id="sugar-value">{{ sugar }}</span
              >g</span
            >
          </p>
          <div class="divider double-indent"></div>
          <p class="double-indent no-divider">
            <span
              >Includes <span id="addedsugar-value">{{ addedSugars }}</span
              >g Added Sugars</span
            ><span class="bold percent" id="addedsugar-percent"
              >{{
                calculatePercentage(
                  addedSugars,
                  percentagesMultipliers["addedsugar-percent"]
                )
              }}%</span
            >
          </p>
          <div class="divider"></div>
          <p class="no-divider">
            <span
              ><span class="bold">Protein </span
              ><span id="protein-value">{{ protein }}</span
              >g</span
            >
          </p>
          <div v-if="includeVitamins" class="vitamins">
            <div class="divider large"></div>
            <p>
              <span
                >Vitamin D <span id="vitd-value">{{ vitaminD }}</span
                >mcg</span
              >
              <span class="percent" id="vitd-percent"
                >{{
                  calculatePercentage(
                    vitaminD,
                    percentagesMultipliers["vitd-percent"]
                  )
                }}%</span
              >
            </p>
            <p>
              <span
                >Calcium <span id="calcium-value">{{ calcium }}</span
                >mg</span
              >
              <span class="percent" id="calcium-percent"
                >{{
                  calculatePercentage(
                    calcium,
                    percentagesMultipliers["calcium-percent"]
                  )
                }}%</span
              >
            </p>
            <p>
              <span
                >Iron <span id="iron-value">{{ iron }}</span
                >mg</span
              ><span class="percent" id="iron-percent"
                >{{
                  calculatePercentage(
                    iron,
                    percentagesMultipliers["iron-percent"]
                  )
                }}%</span
              >
            </p>
            <p class="no-divider">
              <span
                >Potassium <span id="potassium-value">{{ potassium }}</span
                >mg</span
              ><span class="percent" id="potassium-percent"
                >{{
                  calculatePercentage(
                    potassium,
                    percentagesMultipliers["potassium-percent"]
                  )
                }}%</span
              >
            </p>
          </div>
        </div>
        <div class="divider medium"></div>
        <p class="note">
          * The % Daily Value (DV) tells you how much a nutrient in a serving of
          food contributes to a daily diet. 2,000 calories a day is used for
          general nutrition advice.
        </p>
      </div>
    </div>
    <button
      :class="{ 'print-button-disabled': notPrintable }"
      @click="printLabel"
      class="print-button"
      id="print-button"
    >
      Print label
      <p>(Desktop only)</p>
    </button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      notPrintable: true,
      servings: 8,
      size: "2/3 cup",
      weight: 55,
      unit: "g",
      calories: 230,
      fat: 8,
      saturatedFat: 1,
      transFat: 0,
      cholesterol: 0,
      sodium: 160,
      carbohydrate: 37,
      fiber: 4,
      sugar: 12,
      addedSugars: 10,
      protein: 3,
      includeVitamins: true,
      vitaminD: 2,
      calcium: 260,
      iron: 8,
      potassium: 235,
      percentagesMultipliers: {
        "fat-percent": 80,
        "satfat-percent": 20,
        "chol-percent": 300,
        "sodium-percent": 2350,
        "carbo-percent": 310,
        "addedsugar-percent": 50,
        "vitd-percent": 20,
        "calcium-percent": 1300,
        "iron-percent": 18,
        "potassium-percent": 3916,
      },
    };
  },
  methods: {
    formatToNumbers(value) {
      return value.replace(/[^0-9.,]+/gi, "").replace(",", ".");
    },
    printLabel() {
      if (!this.notPrintable) {
        window.print();
      }
    },
    calculatePercentage(element, percent) {
      return ((Math.round(Number(element)) * 100) / percent).toFixed(0);
    },
  },
  created() {
    "ontouchstart" in window || navigator.maxTouchPoints > 0
      ? (this.notPrintable = true)
      : (this.notPrintable = false);
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html,
body {
  min-height: 18em;
  background-color: #f5f5f5;
}

main {
  width: 60%;
  margin: 3rem auto 0 auto;
}

@media screen and (max-width: 1300px) {
  main {
    width: 90%;
    margin: 3rem auto 0 auto;
  }
}

.row:after {
  content: "";
  display: table;
  clear: both;
}

.column {
  float: left;
  width: 50%;
  padding: 10px;
}

@media screen and (max-width: 860px) {
  .column {
    width: 100%;
  }
}

.label-all {
  font-family: "Open Sans", sans-serif;
  background-color: white;
}

.label {
  border: 2px solid black;
  width: 270px;
  margin: 50px auto;
  padding: 0 7px;
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.1), 0 6px 20px 0 rgba(0, 0, 0, 0.2);
}

header h1 {
  text-align: center;
  margin: -4px 0;
  letter-spacing: 0.15px;
}

p {
  margin: 0;
  display: flex;
  justify-content: space-between;
}

.divider {
  border-bottom: 1px solid #888989;
  margin: 2px 0;
}

.bold {
  font-weight: 800;
}

.large {
  height: 10px;
}

.large,
.medium {
  background-color: black;
  border: 0;
}

.medium {
  height: 5px;
}

.small-text {
  font-size: 0.85rem;
}

.calories-info {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
}

.calories-info h2 {
  margin: 0;
}

.left-container p {
  margin: -5px -2px;
  font-size: 2em;
  font-weight: 700;
}

.calories-info span {
  margin: -7px -2px;
  font-size: 2.4em;
  font-weight: 700;
}

.right {
  justify-content: flex-end;
}

.indent {
  margin-left: 1em;
}

.double-indent {
  margin-left: 2em;
}

.daily-value p:not(.no-divider) {
  border-bottom: 1px solid #888989;
}

.note {
  font-size: 0.6rem;
  margin: 5px 0;
  padding: 0 8px;
  text-indent: -8px;
}

form {
  padding: 1rem 0.625rem;
  border-radius: 0.3rem;
  background-color: #fcfcfc;
  margin: auto;
  max-width: 500px;
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.1), 0 6px 20px 0 rgba(0, 0, 0, 0.2);
}

#label-form .divider {
  border-bottom: 1px solid #888989;
  margin: 6px 4px 6px 4px;
}

.form-group {
  margin: 0 auto 0 auto;
  padding: 0.25rem;
}

.form-control {
  display: block;
  width: 100%;
  height: 2rem;
  padding: 0.375rem 0.75rem;
  color: #495057;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

.form-control:focus {
  border-color: grey;
  outline: 0;
  box-shadow: 0 0 0 0.2rem rgba(0, 0, 0, 0.1);
}

.input-radio,
.input-checkbox {
  display: inline-block;
  margin-right: 0.625rem;
  min-height: 1rem;
  min-width: 1rem;
}

#form-column.h1 {
  font-weight: 400;
  line-height: 1.2;
}

#form-column.p {
  font-size: 1.125rem;
}

#form-column.h1,
#form-column.p {
  margin-top: 0;
  margin-bottom: 0.5rem;
}

#form-column.label {
  display: flex;
  align-items: center;
  font-size: 1.125rem;
  margin-bottom: 0.5rem;
}

input,
button,
select,
#form-column.textarea {
  margin: -1px;
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}

label {
  display: flex;
  align-items: center;
  font-size: 1rem;
  color: #595959;
  margin-bottom: 0.2rem;
  font-weight: 700;
}

p.include {
  margin-top: 8px;
  margin-left: 5px;
  margin-bottom: 3px;
}

.print-button {
  margin: 0 auto;
  margin-bottom: 2rem;
  display: block;
  width: 15rem;
  padding: 0.75rem;
  background: #fcfcfc;
  border: none;
  color: rgb(70, 70, 70);
  font-weight: bold;
  border-radius: 4px;
  cursor: pointer;
  transition-duration: 0.6s;
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.1), 0 6px 20px 0 rgba(0, 0, 0, 0.2);
}

.print-button-disabled {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.1), 0 6px 20px 0 rgba(0, 0, 0, 0.2);
  opacity: 0.6;
  cursor: not-allowed;
}

.print-button:hover {
  box-shadow: 0 1px 26px 0 rgba(0, 0, 0, 0.2), 0 12px 40px 0 rgba(0, 0, 0, 0.4);
}

@media print {
  body {
    visibility: hidden;
  }
  #section-to-print {
    visibility: visible;
    position: absolute;
    left: 0;
    top: 0;
    box-shadow: none;
  }
}

.print-button p {
  display: none;
}

.print-button-disabled p {
  display: block;
  margin: 0 auto;
  text-align: center;
  font-size: 0.7rem;
  color: #ff3b3b;
}
</style>
