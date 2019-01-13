<template>
    <div class="input-element-group">
        <label :for="inputId">{{labelText}}</label>
        <input type="text" :name="inputName" :id="inputId" @input="validationMethod" value="">
        <p v-if="hasError" :aria-hidden="!hasError" class="field-error-message">{{errorMessage}}</p>
    </div>
</template>

<script>
export default {
    data: {
        hasError: false
    },
    props: {
        
    },
    methods: {
        validationMethod: function () {
            
        }
    }
}
</script>
