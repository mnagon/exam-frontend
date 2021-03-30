<template>
  <div class="container mx-auto">
    <form
      class="bg-indigo-200 w-2/3 mx-auto rounded-md px-5 py-6 text-center text-gray-600 mb-8"
      @submit.prevent="onSubmit"
    >
      <span class="text-lg font-bold">Test form and validation</span>
      <input-group
        v-model="form.firstName"
        label="First Name"
        type="text"
        placeholder="Please fill first name"
        :danger-message="invalidMessage.firstName"
      />
      <input-group
        v-model="form.lastName"
        label="Last Name"
        type="text"
        placeholder="Please fill last name"
        :danger-message="invalidMessage.lastName"
      />
      <input-group
        v-model="form.email"
        label="E-mail"
        type="email"
        placeholder="Please fill e-mail"
        :danger-message="invalidMessage.email"
      />
      <input-group
        v-model="form.password"
        label="Password"
        type="password"
        placeholder="Please fill password"
        :danger-message="invalidMessage.password"
      />
      <input-group
        v-model="form.verifyPassword"
        label="Verify Password"
        type="password"
        placeholder="Please fill password"
        :danger-message="invalidMessage.verifyPassword"
      />
      <div class="relative">
        <label class="py-2 flex justify-end items-end my-2">
          <span class="font-bold text-gray-600 text-sm">Gender</span>
          <select
            v-model="form.gender"
            :class="[
              'w-4/6 ml-4 px-2 py-1 rounded-sm box-border border-2 border-transparent',
              { 'border-red-400': !!invalidMessage.gender },
            ]"
          >
            <option value="" disabled selected hidden>
              Please select gender
            </option>
            <option value="Male">Male</option>
            <option value="Female">Female</option>
          </select>
        </label>
        <div
          class="w-4/6 text-red-400 text-sm absolute right-0 text-left -bottom-3 italic"
        >
          {{ invalidMessage.gender }}
        </div>
      </div>
      <div class="w-4/6 ml-auto py-3 text-left">
        <button
          class="bg-green-500 text-white px-3 py-1 rounded hover:bg-green-400"
          type="submit"
        >
          Submit
        </button>
      </div>
      <div v-if="isValid" class="text-left mt-3">
        <h3 class="font-bold">Result:</h3>
        <p>First Name: {{ form.firstName }}</p>
        <p>Last Name: {{ form.lastName }}</p>
        <p>E-mail: {{ form.email }}</p>
        <p>Gender: {{ form.gender }}</p>
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
interface Form {
  firstName: string
  lastName: string
  email: string
  password: string
  verifyPassword: string
  gender: string
}
interface State {
  isValid: boolean
  form: Form
  invalidMessage: Form
}

export default Vue.extend({
  data(): State {
    return {
      isValid: false,
      form: this.createFreshForm(),
      invalidMessage: this.createFreshForm(),
    }
  },
  methods: {
    createFreshForm(): Form {
      return {
        firstName: '',
        lastName: '',
        email: '',
        password: '',
        verifyPassword: '',
        gender: '',
      }
    },
    validationForm(): boolean {
      this.invalidMessage = this.createFreshForm()
      Object.keys(this.form).forEach(
        function (key: string): void {
          if (!this.form[key]) {
            this.invalidMessage[key] = 'Please fill out this field.'
          }
        }.bind(this)
      )
      if (this.form.password != this.form.verifyPassword) {
        this.invalidMessage.verifyPassword = 'Verify password is not correct'
      }
      return Object.values(this.invalidMessage).every((e) => !e)
    },
    onSubmit(): void {
      this.isValid = this.validationForm()
    },
  },
})
</script>
