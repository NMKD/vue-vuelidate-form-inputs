<template>
  <div class="container">
    <form class="m-5" @submit.prevent="onSubmit">
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
        <div class="invalid-feedback" v-if="!$v.email.uniqEmail">
          Email is allready exist.
        </div>
      </div>

      <div class="form-group mt-3">
        <label for="password">Password</label>
        <input type="password" name="password" id="password" class="form-control" v-model="password"
          @blur="$v.password.$touch()" :class="{ 'is-invalid': $v.password.$error }">
        <div class="invalid-feedback" v-if="!$v.password.minLength">
          Min length of password {{ $v.password.$params.minLength.min }}. Now is {{ password.length }}
        </div>
      </div>

      <div class="form-group mt-3">
        <label for="confirm">Confirm password</label>
        <input type="confirm" name="confirm" id="confirm" class="form-control" v-model="confirm"
          @blur="$v.confirm.$touch()" :class="{ 'is-invalid': $v.confirm.$error }">
        <div class="invalid-feedback" v-if="!$v.confirm.sameAs">
          Password should match.
        </div>
      </div>
      <button class="btn btn-success m-0 mt-5" type="submit" :disabled="$v.$invalid">Submit</button>
    </form>
  </div>
</template>

<script>
import { required, email, minLength, sameAs } from 'vuelidate/lib/validators'
export default {
  name: "v-form-login",
  data() {
    return {
      email: '',
      password: '',
      confirm: ''
    }
  },
  methods: {
    onSubmit() {
      console.log('Email: ' + this.email)
      console.log('Password: ' + this.password)
    }
  },
  validations: {
    email: {
      required,
      email,
      uniqEmail(newEmail) {
        if (newEmail === '') {
          return true
        }
        // eslint-disable-next-line no-unused-vars
        return new Promise((resolve, reject) => {
          setTimeout(() => {
            const value = newEmail !== 'test@mail.ru'
            resolve(value)
          }, 1000)
        })
      }
    },
    password: {
      minLength: minLength(8)
    },
    confirm: {
      sameAs: sameAs((vue) => {
        return vue.password
      })
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