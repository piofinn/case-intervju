<template>
  <div class="input-element-group">
    <label :for="inputId">{{labelText}}<span v-if="infoText != ''" class="info-button">i</span></label>
    <select :name="inputName" :id="inputId">
      <option selected disabled aria-disabled="true" value="">{{placeholderText}}</option>
      <option v-for="value in values" :key="value" :value="value">{{value}}</option>
    </select>
    <p v-if="hasError" class="field-error-message">{{errorMessage}}</p>
  </div>
</template>

<script>
export default {
  name: "SelectInput",
  data: function() {
    return {
      fieldValue: ""
    };
  },
  props: {
    inputId: String,
    inputName: String,
    labelText: String,
    infoText: {
      type: String,
      default: ''
    },
    placeholderText: String,
    values: Array,
    errorMessage: String,
    isShort: Boolean,
    hasError: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    validationMethod: function() {
      this.hasError = this.fieldValue === "";
    },
    fieldClass: function() {
      var classes = [];
      this.hasError ? classes.push("has-error") : false;
      this.isShort ? classes.push("short") : false;
      return classes.join(" ");
    }
  }
};
</script>

<style lang="scss">
span.info-button {
  display: inline-block;
  margin-left: 1rem;
  cursor: pointer;
  height: 32px;
  width: 32px;
  border: 1px solid #ccc;
  border-radius: 100%;
  font-size: 1.25rem;
  text-align: center;
  color: #0075d2;
  line-height: 32px;
}
</style>
