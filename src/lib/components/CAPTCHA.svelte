<script lang="ts">
  import { captchas } from "$lib/captchas";
  import { fade } from "svelte/transition";
</script>

<div class="absolute border border-neutral-200 bg-white z-10 bottom-4 left-16 w-[25rem] text-white" transition:fade>
  <div class="p-1">
    <!-- Instructions -->
    <section class="bg-blue-600 h-20 w-full flex flex-col justify-center px-4">
      <h2>Select all images with</h2>
      <h1 class="font-bold text-2xl">taxis</h1>
    </section>

    <!-- The actual grid -->
    <section class="aspect-square w-full grid grid-cols-3 grid-rows-3 text-black">
      stuff
    </section>

    <hr>

    <!-- Buttons and stuff -->
    <section class="flex justify-between m-1">
      <div>
        <!-- Imaginary options -->
      </div>

      <button class="uppercase bg-blue-600 p-2 px-6 rounded-sm font-semibold text-sm">
        Verify
      </button>
    </section>
  </div>
</div>
