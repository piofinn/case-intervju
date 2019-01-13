<template>
  <div class="input-element-group">
    <label :for="inputId">{{labelText}}</label>
    <input
      type="text"
      :class="fieldClass()"
      :name="inputName"
      :id="inputId"
      v-model="fieldValue"
      @change="validationMethod"
      :placeholder="placeholderText"
    >
    <p v-if="hasError" class="field-error-message">{{errorMessage}}</p>
  </div>
</template>

<script>
export default {
  name: "TextInput",
  data: function() {
    return {
      hasError: false,
      fieldValue: ""
    };
  },
  props: {
    inputId: String,
    inputName: String,
    labelText: String,
    placeholderText: String,
    errorMessage: String,
    validationRegex: RegExp,
    isShort: Boolean
  },
  methods: {
    validationMethod: function() {
      this.hasError = !this.fieldValue.match(this.validationRegex);
    },
    fieldClass: function() {
      var classes = [];
      this.hasError ? classes.push("has-error") : false;
      this.isShort ? classes.push("short") : false;
      console.log(classes.join(" "));

      return classes.join(" ");
    }
  }
};
</script>