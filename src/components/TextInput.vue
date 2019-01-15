<template>
  <div class="input-element-group">
    <label :for="inputId">{{labelText}}</label>
    <input
      type="text"
      :class="fieldClass()"
      :name="inputName"
      :id="inputId"
      @change="$emit('input', $event.target.value)"
      :placeholder="placeholderText"
    >
    <p v-if="hasError" class="field-error-message">{{errorMessage}}</p>
  </div>
</template>

<script>
export default {
  name: "TextInput",
  props: {
    value: {
      type: String,
      default: ""
    },
    inputId: String,
    inputName: String,
    labelText: String,
    placeholderText: String,
    errorMessage: String,
    validationRegex: RegExp,
    isShort: Boolean,
    hasError: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    validationMethod: function() {
      this.hasError =
        !this.fieldValue.match(this.validationRegex) || this.fieldValue === "";
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