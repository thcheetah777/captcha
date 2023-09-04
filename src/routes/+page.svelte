<script lang="ts">
  import "iconify-icon";
  import { fade, slide } from "svelte/transition";
  import Captcha from "$components/CAPTCHA.svelte";

  let formLoading = false;
  let formDisabled = false;
  let formCaptcha = true;
  let captcha = true;

  function submitForm() {
    formLoading = true;
    formDisabled = true;

    setTimeout(() => {
      formLoading = false;
      formCaptcha = true;
    }, 4000);
  }
</script>

<div class="flex justify-center items-center h-full">
  <main class="bg-white shadow-lg p-8 rounded-md w-1/2 space-y-8">
    <h1 class="text-xl font-bold">Create a new account</h1>
    <hr>

    <!-- Fake form -->
    <form on:submit={submitForm}>
      <label for="email" class="space-y-1">
        <span class="font-medium">Your email address</span>
        <input
          type="email"
          id="email"
          class="block w-full outline-none border-neutral-300 focus:border-blue-600 duration-200 border-2 p-2 text-sm rounded-sm"
          required />
      </label>

      <br>

      <label for="password" class="space-y-1">
        <span class="font-medium">Password</span>
        <input
          type="password"
          id="password"
          class="block w-full outline-none border-neutral-300 focus:border-blue-600 duration-200 border-2 p-2 text-sm rounded-sm"
          required />
      </label>

      <br>

      <label for="repeatPassword" class="space-y-1">
        <span class="font-medium">Repeat password</span>
        <input
          type="password"
          id="repeatPassword"
          class="block w-full outline-none border-neutral-300 focus:border-blue-600 duration-200 border-2 p-2 text-sm rounded-sm"
          required />
      </label>

      <br>

      {#if formCaptcha}
        <div
          class="border-neutral-200 bg-neutral-100 border rounded-sm shadow-md p-6 relative"
          transition:slide={{ duration: 500 }}>
          <label class="font-semibold flex items-center gap-4">
            <button
              class="border-2 border-neutral-400 w-8 h-8 rounded-sm bg-white"
              on:click|preventDefault={() => captcha = true}></button>
            <span>I'm not a robot</span>
          </label>

          {#if captcha}
            <Captcha />
          {/if}
        </div>
      {/if}

      <br>

      <button
        type="submit"
        class={
          `text-white duration-200 px-4 py-2 rounded-sm flex items-center gap-2
          ${formDisabled ? "bg-neutral-600" : "bg-blue-600 hover:bg-blue-700 active:bg-blue-800"}`
        }
        disabled={formDisabled}>
        {#if formLoading}
          <iconify-icon icon="gg:spinner-alt" class="animate-spin text-lg"></iconify-icon>
        {/if}

        Create account
      </button>
    </form>
  </main>
</div>
