<script lang="ts">
  type Skill = {
    img: string,
    name: string
  }
  import typescript from "../lib/assets/typescript.svg"
  import svelteLogo from "../lib/assets/svelte.svg"
  import elixir from "../lib/assets/elixir.svg"
  import zig from "../lib/assets/zig.svg"
  // State variables using Svelte 5 Runes ($state)
  let name = $state('SVELTE'); // Simplified $state declaration
  // hereKitty state removed, replaced by pure CSS hover logic for reliability.
  let skills: Array<Skill> = [{img: typescript, name: "TypeScript"}, {img: svelteLogo, name: "Svelte"}, {img: elixir, name: "Elixir"}, {img: zig, name: "Zig"}];
 
  // State for custom message box (replacing alert)
  let showMessage = $state(false);
  let message = $state('');
  
  // The asset path is relative to src/routes/+page.svelte
  // The build tool (Vite/SvelteKit) will handle this import.
  import kitty from "../lib/assets/Asian_tabby_cat_transparent.webp"

  /**
   * Toggles the case of the name string.
   */
  function fart() {
    if (isAllUppercase(name)) {
      name = name.toLowerCase();
    } else {
      name = name.toUpperCase();
    }
  }

  /**
   * Checks if a string contains only uppercase letters, numbers, and symbols.
   * @param str The string to check.
   */
  function isAllUppercase(str: string): boolean {
    // Note: The regex is adjusted slightly for clarity, but preserves the original intent.
    return /^[A-Z0-9!@#$%^&*()_+\-=\[\]{};':"\\|,.<>\/?]*$/.test(str);
  }
  
  /**
   * Handles the cat click event, showing a custom message instead of alert().
   */
  function onclick() {
    message = 'Meow! (Clicking the button runs a function)';
    showMessage = true;
    
    // Auto-hide the message after 2 seconds
    setTimeout(() => {
      showMessage = false;
    }, 2000);
  }
</script>

<!-- Global event listeners on the body element were removed -->
<!-- The cat effect is now triggered by hovering over the 'portfolio-main' container via CSS. -->

<!-- Main Layout Container (Given a class for CSS targeting) -->
<div class="portfolio-main p-8 max-w-7xl mx-auto min-h-screen flex flex-col justify-center bg-black text-white font-sans">
  <h1 class="text-5xl md:text-6xl font-extrabold mb-0 m-4 ml-0 leading-tight">
    Miles Knaebe
  </h1>
  <span class="text-lg">aka. thaiiko</span>
  <span class="font-normal block text-3xl mt-2">
    powered by
    <button 
      onclick={fart} 
      class="text-amber-400 hover:text-amber-300 transition-colors bg-transparent border-none p-0 align-baseline"
    > 
      {name} 
    </button>
    </span>
  
  <!-- Skills Section -->
  <div class="skills text-xl inline-block mt-4 mb-8 p-4 bg-gray-900/50 rounded-xl shadow-lg">
    <h2 class="text-3xl font-semibold mb-2 text-amber-500">Skills</h2>
    <ul class="font-light  ml-6 space-y-1">
      {#each skills as skill}
        <li class="hover:font-medium transition-all duration-150 w-[100px] h-auto">{skill.name}<img title={skill.name} src={skill.img}></li>
      {/each}
    </ul>
  </div>

  <!-- Github Link (SVG scaled down for better placement) -->
  <a 
    href="https://github.com/thaiiko" 
    target="_blank" 
    title="Github Link"
    class="block w-16 h-16 hover:scale-110 transition-transform duration-300 ease-in-out"
  >
    <svg width='64' height='64' viewBox='0 0 1024 1024' fill='none' xmlns='http://www.w3.org/2000/svg'> <path fill-rule='evenodd' clip-rule='evenodd' d='M8 0C3.58 0 0 3.58 0 8C0 11.54 2.29 14.53 5.47 15.59C5.87 15.66 6.02 15.42 6.02 15.21C6.02 15.02 6.01 14.39 6.01 13.72C4 14.09 3.48 13.23 3.32 12.78C3.23 12.55 2.84 11.84 2.5 11.65C2.22 11.5 1.82 11.13 2.49 11.12C3.12 11.11 3.57 11.7 3.72 11.94C4.44 13.15 5.59 12.81 6.05 12.6C6.12 12.08 6.33 11.73 6.56 11.53C4.78 11.33 2.92 10.64 2.92 7.58C2.92 6.71 3.23 5.99 3.74 5.43C3.66 5.23 3.38 4.41 3.82 3.31C3.82 3.31 4.49 3.1 6.02 4.13C6.66 3.95 7.34 3.86 8.02 3.86C8.7 3.86 9.38 3.95 10.02 4.13C11.55 3.09 12.22 3.31 12.22 3.31C12.66 4.41 12.38 5.23 12.3 5.43C12.81 5.99 13.12 6.7 13.12 7.58C13.12 10.65 11.25 11.33 9.47 11.53C9.76 11.78 10.01 12.26 10.01 13.01C10.01 14.08 10 14.94 10 15.21C10 15.42 10.15 15.67 10.55 15.59C13.71 14.53 16 11.53 16 8C16 3.58 12.42 0 8 0Z' transform='scale(64)' fill='#ffff' /> </svg>
  </a>
</div>

<!-- Custom Message Box (replacing alert()) -->
{#if showMessage}
<div class="fixed top-4 right-4 z-50 p-4 bg-amber-500 text-black rounded-lg shadow-2xl transition-opacity duration-300"
     role="alert"
     aria-live="polite"
>
  <p class="font-semibold">{message}</p>
</div>
{/if}

<!-- Kitty Button (Clickable) -->
<button 
  onclick={onclick} 
  aria-label="cat"
  class="bg-transparent border-none p-0 cursor-pointer hidden md:block"
>
  <img
    src={kitty}
    alt="Asian Tabby Cat"
    id="kitty"
  />
    <!-- class:curious={hereKitty} removed -->

</button>

<style>
  /* Base styles for the cat image */
  img#kitty {
    position: fixed; 
    left: 0;
    bottom: -5in; 
    height: 40rem; 
    width: 4in; 
    max-height: 80vh; 
    max-width: 50vw; 
    object-fit: contain;
    
    /* Initial transformation: tucked away */
    transform: translate(-80%, 0) rotate(-30deg);
    transform-origin: 100% 100%;
    transition: transform 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  }

  /*
    NEW LOGIC: 
    When hovering over the main content (.portfolio-main) 
    OR the cat button itself, apply the 'curious' transform.
    The `~` (general sibling selector) is used because the button 
    is a sibling that appears later in the DOM than the div.
  */
  .portfolio-main:hover ~ button img#kitty,
  button:hover img#kitty {
    /* New position: peeking out */
    transform: translate(-50%, 0) rotate(15deg);
  }

  /* Global style to prevent body scrollbars if content doesn't fit */
  :global(body) {
    font-family: ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif;
  }
</style>
