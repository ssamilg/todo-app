<script>
import { reactive, toRefs } from 'vue';
import { useRouter } from 'vue-router';

export default {
  name: 'LoginView',
  setup() {
    const router = useRouter();
    const state = reactive({
      email: '',
      password: '',
      isPasswordVisible: false,
    });

    const togglePasswordVisibility = () => {
      state.isPasswordVisible = !state.isPasswordVisible;
    };

    const login = () => {
      const formData = {
        email: state.email,
        password: state.password,
      };

      console.log('login');
      console.log(formData);

      // ...
      router.push('/');
    };

    return { ...toRefs(state), login, togglePasswordVisibility };
  },
};
</script>

<template>
  <div id="login-view">
    <div class="flex flex-row items-center justify-center h-full">
      <div class="basis-1/3">
        <div class="card w-full bg-base-200">
          <div class="card-body">
            <h2 class="card-title justify-center">Login</h2>

            <input
              v-model="email"
              type="text"
              placeholder="Email"
              class="input input-bordered w-full focus:outline-none mt-2"
            />

            <input
              v-model="password"
              :type="isPasswordVisible ? 'text' : 'password'"
              placeholder="Password"
              class="input input-bordered w-full focus:outline-none mt-2"
            />

            <div class="cursor-pointer hover:underline text-right" @click="togglePasswordVisibility">
              {{ isPasswordVisible ? 'Hide' : 'Show' }}
              Password
            </div>

            <div class="flex flex-row text-center mt-2">
              <router-link to="/register">Don't have an account? Register now.</router-link>
            </div>

            <div class="card-actions justify-end mt-2">
              <button class="btn btn-primary w-full" @click="login">
                Login
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