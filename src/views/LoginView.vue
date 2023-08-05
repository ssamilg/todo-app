<script>
export default {
  name: 'LoginView',
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
              type="text"
              placeholder="Email"
              class="input input-bordered w-full focus:outline-none mt-2"
            />

            <input
              type="password"
              placeholder="Password"
              class="input input-bordered w-full focus:outline-none mt-2"
            />


            <div class="card-actions justify-end mt-2">
              <button class="btn btn-primary w-full">Login</button>
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