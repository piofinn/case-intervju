<template>
  <div id="app" class="container">
    <h1>Kjøp bilforsikring</h1>
    <p class="intro">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut non libero quis erat ultricies dictum nec ut massa. Etiam nec sapien leo. Vestibulum risus arcu, pretium ut dui tincidunt, accumsan blandit metus. Cras eget imperdiet eros.</p>
    <form action v-if="!formSubmitted">
      <text-input
        isShort
        input-id="reg-nummer"
        input-name="registreringsnummer"
        label-text="Bilens registreringsnummer"
        placeholder-text="AB12345"
        :validation-regex="/^[a-zA-Z]{2}\d{5}$/g"
        error-message="Registreringsnummeret må bestå av to bokstaver og fem tall"
      />
      <text-input
        input-id="bonus"
        input-name="bonus"
        label-text="Din bonus"
      />
      <text-input
        isShort
        input-id="f-nummer"
        input-name="fodselsnummer"
        label-text="Fødselsnummer"
        :validation-regex="/^\d{11}$/g"
        error-message="Fødselsnummeret må bestå av elleve tall"
      />
      <div class="form-row">
        <div class="col col-12 col-sm-4">
          <text-input
            input-id="fornavn"
            input-name="fornavn"
            label-text="Fornavn"
          />
        </div>
        <div class="col col-12 col-sm-4">
          <text-input
            input-id="etternavn"
            input-name="etternavn"
            label-text="Etternavn"
          />
        </div>
        <div class="col-sm-auto"></div>
      </div>  
    </form>
  </div>
</template>

<script>
import TextInput from "./components/TextInput.vue"

export default {
  components: {
    TextInput
  },
  data: function() {
    return {
      formSubmitted: false
    }
  }
}
</script>

<style lang="scss">
@import 'minireset';

h1 {
  font-size: 3rem;
  text-align: center;
  padding: 0.5em;
}
</style>
