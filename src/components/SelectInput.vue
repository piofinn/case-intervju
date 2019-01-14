<template>
  <div class="input-element-group">
    <label :for="inputId">
      {{labelText}}
      <span v-if="infoText != ''" class="info-button" @click="toggleInfo">i</span>
      <span v-if="showInfo" class="info-text">{{infoText}}</span>
    </label>
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
      fieldValue: "",
      showInfo: false
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
    },
    toggleInfo: function() {
      this.showInfo = !this.showInfo;
    }
  }
};
</script>

<style lang="scss">
span {
  &.info-button {
    display: inline-block;
    margin-left: 0.5rem;
    cursor: pointer;
    height: 32px;
    min-width: 32px;
    border: 1px solid #ccc;
    border-radius: 16px;
    font-size: 1.25rem;
    text-align: center;
    color: #0075d2;
    line-height: 32px;
  }

  &.info-text {
    display: inline-block;
    position: relative;
    margin: 0 0 0 0.5rem;
    padding: 0 1em;
    height: 32px;
    background-color: rgba(0,0,0,0.75);
    box-shadow: 0 1px 1px 0 rgba(0,0,0,0.25);
    border-radius: 5px;
    color: #fff;
    font-size: 1rem;
    line-height: 32px;
  }
}
</style>
