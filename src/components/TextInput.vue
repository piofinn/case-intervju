<template>
  <div class="input-element-group">
    <label :for="inputId">{{labelText}}</label>
    <input
      type="text"
      :class="{'has-error': hasError, short: isShort}"
      :name="inputName"
      :id="inputId"
      @input="$emit('input', $event.target.value)"
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
  }
};
</script>