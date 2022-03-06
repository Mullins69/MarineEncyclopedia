<template>
  <section id="Login">
    <div
      class="container "
      aria-hidden="false"
      aria-label="Dialog open. Sign in to start taking action"
    >
      <div class="row">
        <div class="col">
          <p>
            Welcome back!
            <br />
            Sign in to start taking action.
          </p>
          <p>
            Not a ME Citizen yet?
            <a
              href="#"
              aria-label="Not a Global Citizen yet? Sign up."
              >Sign up</a
            >
          </p>
          <div class="horizontal-rule-with-text">
            <hr />
            <span>or</span>
            <hr />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col">
          <form method="POST" action="/account/login/">
              <div id="login-fields">

                  <div class="mb-4" >
                    <div class="">
                      <input
                        type="email"
                        aria-label="Email Address"

                        required
                        placeholder="Email Address"
                      />
                    </div>
                  </div>
                  <div class="mb-4" >
                    <input
                      type="password"
                      required
                      aria-label="Password"
                      placeholder="Password"
                    />
                  </div>
                  <button
                    class="btn btn-primary w-100 mb-2 text-uppercase"
                    type="submit"
                    aria-label="Sign In"
                  >
                    <span class=""><span class="">Sign In</span></span>
                  </button>

              </div>

            <fieldset class="text-left">
              <p class="mt-4">
                <a href="/account/password/reset/" id="forgotPassword"
                  >Forget your password?</a
                >
              </p>
            </fieldset>
          </form>
        </div>
      </div>
       <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
    </div>
  </section>
</template>

<script>
export default {
    
};
</script>

<style scoped>

.container {
  display: grid;
  width: 50%;
  min-width: 50%;
  justify-content: center;
  align-content: center;
  text-align: left;
  min-height: 100%;
  margin: auto;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;

  background: rgba(247, 247, 247, 0.97);
  box-shadow: none;
  border: 0;
  overflow-y: auto;
}

.horizontal-rule-with-text{
    display: grid;
    justify-content: center;
}
form{
    margin: 0 2px;
}
</style>