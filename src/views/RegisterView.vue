<script>
import { reactive, toRefs } from 'vue';

export default {
  name: 'LoginView',
  setup() {
    const state = reactive({
      email: '',
      password: '',
      name: '',
      surname: '',
    });

    const login = () => {
      const formData = {
        email: state.email,
        password: state.password,
        name: state.name,
        surname: state.surname,
      };

      console.log('register');
      console.log(formData);
    };

    return { ...toRefs(state), login };
  },
};
</script>

<template>
  <div id="login-view">
    <div class="flex flex-row items-center justify-center h-full">
      <div class="basis-1/3">
        <div class="card w-full bg-base-200">
          <div class="card-body">
            <h2 class="card-title justify-center">Register</h2>

            <input
              v-model="name"
              type="text"
              placeholder="Name"
              class="input input-bordered w-full focus:outline-none mt-2"
            />

            <input
              v-model="surname"
              type="text"
              placeholder="Surname"
              class="input input-bordered w-full focus:outline-none mt-2"
            />

            <input
              v-model="email"
              type="text"
              placeholder="Email"
              class="input input-bordered w-full focus:outline-none mt-2"
            />

            <input
              v-model="password"
              type="password"
              placeholder="Password"
              class="input input-bordered w-full focus:outline-none mt-2"
            />

            <div class="flex flex-row text-center mt-2">
              <router-link to="/login">Already have an account? Login</router-link>
            </div>

            <div class="card-actions justify-end mt-2">
              <button class="btn btn-primary w-full" @click="login">
                Register
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
#login-view {
  height: 100%;
}
</style>