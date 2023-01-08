<template>
  <div class="container">
    <form action="" class="p-3 mt-5">
      <div class="form-group">
        <label for="email">Email</label>
        <input type="email" name="email" id="email" class="form-control" v-model="email" @blur="$v.email.$touch()"
          :class="{ 'is-invalid': $v.email.$error }">
        <div class="invalid-feedback" v-if="!$v.email.email">
          Please provide a valid email.
        </div>
        <div class="invalid-feedback" v-if="!$v.email.required">
          Email is required.
        </div>
      </div>
    </form>
  </div>
</template>

<script>
import { required, email } from 'vuelidate/lib/validators'
export default {
  name: "v-button-conroller",
  data() {
    return {
      email: ''
    }
  },
  validations: {
    email: {
      required,
      email
    }
  }
}
</script>

<style scoped>
.btn {
  padding: 1rem 1.5rem;
  margin: 1rem;
  font-size: 20px;
  font-weight: 600;
  border: none;
}

.btn-on {
  background: #73A353;
  color: #fff;
  border: 1px solid aqua;
}

button.btn-off {
  background: #C1172C;
  color: #fff;
  border: 1px solid royalblue;
}
</style>