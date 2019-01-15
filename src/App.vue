<template>
  <div id="app" class="container">
    <h1>Kjøp bilforsikring</h1>
    <p
      class="intro"
    >Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut non libero quis erat ultricies dictum nec ut massa. Etiam nec sapien leo. Vestibulum risus arcu, pretium ut dui tincidunt, accumsan blandit metus. Cras eget imperdiet eros.</p>
    <form action v-if="!formSubmitted">
      <text-input
        isShort
        input-id="input-reg-nummer"
        input-name="registreringsnummer"
        label-text="Bilens registreringsnummer"
        placeholder-text="AB12345"
        :validation-regex="/^[a-zA-Z]{2}\d{5}$/g"
        error-message="Registreringsnummeret må bestå av to bokstaver og fem tall"
        v-model="registration"
        :has-error="$v.fodselsnummer.$error"
      />
      <select-input
        input-id="input-bonus"
        input-name="bonus"
        label-text="Din bonus"
        info-text="Startbonus er 40%"
        error-message="Påkrevd felt"
        placeholder-text="Velg din bonus"
        :values="bonusValues"
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
            input-id="input-fornavn"
            input-name="fornavn"
            label-text="Fornavn"
            error-message="Påkrevd felt"
            v-model="firstName"
          />
        </div>
        <div class="col col-12 col-sm-4">
          <text-input
            input-id="input-etternavn"
            input-name="etternavn"
            label-text="Etternavn"
            error-message="Påkrevd felt"
            v-model="lastName"
          />
        </div>
        <div class="col-sm-auto"></div>
      </div>
      <text-input
        input-id="epost"
        input-name="epost"
        label-text="E-post"
        :validation-regex="/[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}/g"
        error-message="Skriv inn en gyldig epostadresse"
      />
      <button class="button-submit" @click.prevent="checkForm">Beregn Pris</button>
      <button class="button-abort" @click.prevent>Avbryt</button>
    </form>
  </div>
</template>

<script>
import TextInput from "./components/TextInput.vue";
import SelectInput from "./components/SelectInput.vue";
import { required, email, helpers } from "vuelidate/lib/validators";

const regNumberVal = value => value.match(/^[a-zA-Z]{2}\d{5}$/g);
const fNumberVal = helpers.regex('fNumberVal', /^\d{11}$/g);

export default {
  components: {
    TextInput,
    SelectInput
  },
  data: function() {
    return {
      formSubmitted: false,
      bonusValues: ["40%", "50%", "60%", "70%"],

      registration: "",
      bonusValue: "",
      fodselsnummer: "",
      firstName: "",
      lastName: "",
      emailAddress: ""
    };
  },
  validations: {
    registration: {
      required,
      regNumberVal
    },
    bonusValue: {
      required
    },
    fodselsnummer: {
      required,
      fNumberVal
    },
    firstName: {
      required
    },
    lastName: {
      required
    },
    emailAddress: {
      required,
      email
    }
  },
  methods: {
    checkForm() {
      return false;
    }
  }
};
</script>

<style lang="scss">
@import "minireset";

h1 {
  font-size: 3rem;
  text-align: center;
  padding: 0.5em;
}

form {
  margin-bottom: 2rem;
}

button {
  height: 44px;
  border-radius: 3px;
  border: none;
  padding: 0 1.5em;
  margin-right: 1rem;

  &:focus {
    outline: none;
  }

  &.button-submit {
    background-color: #0075d2;
    color: #fff;

    &:active {
      background-color: #002776;
    }
  }

  &.button-abort {
    border: 2px solid #ccc;
    background-color: #fff;
    color: #0075d2;

    &:active {
      background-color: #ccc;
    }
  }
}
</style>
