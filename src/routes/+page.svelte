<script lang="ts">
  let name: string = $state("Svelte");
  let hereKitty: boolean = $state(true);
  import kitty from "/src/lib/assets/Asian_tabby_cat_transparent.webp"
  // import github from "/src/lib/assets/github_dark.svg"

  function fart() {
    if (isAllUppercase(name)) {
      name = name.toLowerCase();
    } else {
      name = name.toUpperCase();
    }
  }

  let skills: Array<string> = ["TypeScript", "Svelte", "Elixir", "C & C++", "Zig"]
  function isAllUppercase(str: string) {
      return /^[A-Z0-9!@#$%^&*()_+\-=\[\]{};':"\\|,.<>\/?]*$/.test(str);
  }
</script>
     
   
 
     
<div class="p-8 max-w-7xl h-screen justify-center bg-black text-white jetbrains-mono-foont">
  <h1 class="text-6xl flex-9 ">
    Miles Knaebe aka. thaiiko
     built with <button onclick={fart}> {name} </button>
  </h1>
  <div class="skills text-xl inline-block" >
    <h2> Skills </h2>
    <ul class="font-normal list-disc m-3"> 
      {#each skills as skill}
        <li class="hover:font-extrabold fit-content">{skill}</li>
      {/each}
    </ul>
  </div>

  <a href="https://github.com/thaiiko" target="_blank" hreflang="en" title="Github Link">
  <svg width='64' height='64' viewBox='0 0 1024 1024' fill='none' xmlns='http://www.w3.org/2000/svg'>
    <path
      fill-rule='evenodd'
      clip-rule='evenodd'
      d='M8 0C3.58 0 0 3.58 0 8C0 11.54 2.29 14.53 5.47 15.59C5.87 15.66 6.02 15.42 6.02 15.21C6.02 15.02 6.01 14.39 6.01 13.72C4 14.09 3.48 13.23 3.32 12.78C3.23 12.55 2.84 11.84 2.5 11.65C2.22 11.5 1.82 11.13 2.49 11.12C3.12 11.11 3.57 11.7 3.72 11.94C4.44 13.15 5.59 12.81 6.05 12.6C6.12 12.08 6.33 11.73 6.56 11.53C4.78 11.33 2.92 10.64 2.92 7.58C2.92 6.71 3.23 5.99 3.74 5.43C3.66 5.23 3.38 4.41 3.82 3.31C3.82 3.31 4.49 3.1 6.02 4.13C6.66 3.95 7.34 3.86 8.02 3.86C8.7 3.86 9.38 3.95 10.02 4.13C11.55 3.09 12.22 3.31 12.22 3.31C12.66 4.41 12.38 5.23 12.3 5.43C12.81 5.99 13.12 6.7 13.12 7.58C13.12 10.65 11.25 11.33 9.47 11.53C9.76 11.78 10.01 12.26 10.01 13.01C10.01 14.08 10 14.94 10 15.21C10 15.42 10.15 15.67 10.55 15.59C13.71 14.53 16 11.53 16 8C16 3.58 12.42 0 8 0Z'
      transform='scale(64)'
      fill='#ffff'
    />
</svg>
  </a>
  <a href="https://tiktok.com/@thaiko.mp4" target="_blank" hreflang="en">
    <span>
      Tiktok
    </span>
  </a>
</div>

<svelte:body 
  onmouseenter={() => {
    hereKitty = true;
  }}
  onmouseleave={() => {
    hereKitty = false;
  }}
/>

<!-- CC-ASA4I License converted to webp https://commons.wikimedia.org/wiki/File:Asian_tabby_cat_transparent.png -->

<img
  src={kitty} 
  alt="cat"
  class={{curious: hereKitty}}
/>

<style>
  img {
		position: absolute;
		left: 0;
		bottom: -0.5in;
    height: 6.16867469879in;
    width: 4in;
		transform: translate(-80%, 0) rotate(-30deg);
		transform-origin: 100% 100%;
		transition: transform 0.8s;
	}

	.curious {
		transform: translate(-2%, 0) rotate(15deg);
	}

	:global(body) {
		overflow: hidden;
	}
</style>

