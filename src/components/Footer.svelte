<script>
  import { fade, fly } from 'svelte/transition';
  let firstName = '';
  let email = '';
  let isSubmitting = false;
  let done = false;
  const social = [
    {
      href: 'https://github.com/22mahmoud/',
      name: 'github',
      icon: `<svg class="w-6 h-6 " viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg"><path d="M256 0C115.39 0 0 115.39 0 256c0 119.988 84.195 228.984 196 256v-84.695c-11.078 2.425-21.273 2.496-32.55-.828-15.13-4.465-27.423-14.543-36.548-29.91-5.816-9.813-16.125-20.454-26.879-19.672l-2.636-29.883c23.254-1.992 43.37 14.168 55.312 34.23 5.305 8.922 11.41 14.153 19.246 16.465 7.575 2.23 15.707 1.16 25.184-2.187 2.379-18.973 11.07-26.075 17.637-36.075v-.015c-66.68-9.946-93.254-45.32-103.801-73.242-13.977-37.075-6.477-83.391 18.238-112.66.48-.571 1.348-2.063 1.012-3.106-11.332-34.23 2.476-62.547 2.984-65.55 13.078 3.866 15.203-3.892 56.809 21.386l7.191 4.32c3.008 1.793 2.063.77 5.07.543 17.372-4.719 35.684-7.324 53.727-7.558 18.18.234 36.375 2.84 54.465 7.75l2.328.234c-.203-.031.633-.149 2.035-.984 51.973-31.481 50.106-21.192 64.043-25.723.504 3.008 14.13 31.785 2.918 65.582-1.512 4.656 45.059 47.3 19.246 115.754-10.547 27.933-37.117 63.308-103.797 73.254v.015c8.547 13.028 18.817 19.957 18.762 46.832V512c111.809-27.016 196-136.012 196-256C512 115.39 396.61 0 256 0zm0 0"/></svg>`,
    },
    {
      href: 'https://twitter.com/_22mahmoud/',
      name: 'twitter',
      icon: `<svg class="w-6 h-6" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M512 97.248c-19.04 8.352-39.328 13.888-60.48 16.576 21.76-12.992 38.368-33.408 46.176-58.016-20.288 12.096-42.688 20.64-66.56 25.408C411.872 60.704 384.416 48 354.464 48c-58.112 0-104.896 47.168-104.896 104.992 0 8.32.704 16.32 2.432 23.936-87.264-4.256-164.48-46.08-216.352-109.792-9.056 15.712-14.368 33.696-14.368 53.056 0 36.352 18.72 68.576 46.624 87.232-16.864-.32-33.408-5.216-47.424-12.928v1.152c0 51.008 36.384 93.376 84.096 103.136-8.544 2.336-17.856 3.456-27.52 3.456-6.72 0-13.504-.384-19.872-1.792 13.6 41.568 52.192 72.128 98.08 73.12-35.712 27.936-81.056 44.768-130.144 44.768-8.608 0-16.864-.384-25.12-1.44C46.496 446.88 101.6 464 161.024 464c193.152 0 298.752-160 298.752-298.688 0-4.64-.16-9.12-.384-13.568 20.832-14.784 38.336-33.248 52.608-54.496z"/></svg>`,
    },
    {
      href: 'https://www.linkedin.com/in/22mahmoud/',
      name: 'linkedin',
      icon:
        '<svg class="w-6 h-6" height="512pt" viewBox="0 0 512 512" width="512pt" xmlns="http://www.w3.org/2000/svg"><path d="M256 0C114.637 0 0 114.637 0 256s114.637 256 256 256 256-114.637 256-256S397.363 0 256 0zm-74.39 387h-62.348V199.426h62.347zm-31.173-213.188h-.406c-20.922 0-34.453-14.402-34.453-32.402 0-18.406 13.945-32.41 35.274-32.41 21.328 0 34.453 14.004 34.859 32.41 0 18-13.531 32.403-35.274 32.403zM406.423 387h-62.34V286.652c0-25.218-9.027-42.418-31.586-42.418-17.223 0-27.48 11.602-31.988 22.801-1.649 4.008-2.051 9.61-2.051 15.215V387h-62.344s.817-169.977 0-187.574h62.344v26.558c8.285-12.78 23.11-30.96 56.188-30.96 41.02 0 71.777 26.808 71.777 84.421zm0 0"/></svg>',
    },
    {
      href: 'mailto:hello@mahmoudashraf.dev',
      name: 'email',
      icon: `<svg class="w-6 w-6" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M467 61H45c-6.927 0-13.412 1.703-19.279 4.51L255 294.789l51.389-49.387.005-.007.005-.004L486.286 65.514C480.418 62.705 473.929 61 467 61zM507.496 86.728L338.213 256.002 507.49 425.279c2.807-5.867 4.51-12.352 4.51-19.279V106c0-6.923-1.699-13.407-4.504-19.272zM4.51 86.721C1.703 92.588 0 99.073 0 106v300c0 6.923 1.701 13.409 4.506 19.274L173.789 256 4.51 86.721z"/><path d="M317.002 277.213l-51.396 49.393c-2.93 2.93-6.768 4.395-10.605 4.395s-7.676-1.465-10.605-4.395L195 277.211 25.714 446.486C31.582 449.295 38.071 451 45 451h422c6.927 0 13.412-1.703 19.279-4.51L317.002 277.213z"/></svg>`,
    },
  ];

  function handleSubmit() {
    isSubmitting = true;
    if (email && firstName) {
      fetch('/.netlify/functions/mailgun', {
        method: 'POST',
        headers: {
          'content-type': 'application/json',
        },
        body: JSON.stringify({ email, name: firstName }),
      }).then(() => {
        isSubmitting = false;
        done = true;
      });
    }
  }
</script>

<div class="flex flex-wrap">
  <div class="flex-1 flex flex-col p-8 bg-gray-800 shadow-xs rounded">
    {#if !done}
      <div transition:fade="{{ duration: 400 }}">
        <h3 class="text-xl mb-8">Join the Newsletter 📰</h3>
        <form
          on:submit|preventDefault="{handleSubmit}"
          class="flex flex-col"
          name="subscription"
        >
          <label for="firstName" class="mb-2">First Name</label>
          <input
            bind:value="{firstName}"
            required
            class="mb-3"
            id="firstName"
            name="firstName"
            placeholder="Mahmoud"
            type="text"
          />
          <label for="email" class="mb-2">Email</label>
          <input
            bind:value="{email}"
            required
            id="email"
            name="email"
            placeholder="mahmoud@test.com"
            type="email"
          />
          <button
            disabled="{isSubmitting}"
            class="self-start px-5 py-3 bg-gray-700 rounded text-gray-200 mt-4
            text-lg pointer shadow-xs hover:bg-gray-600 transition-all
            duration-200 ease-in"
            type="submit"
          >
            {#if isSubmitting}loading...{:else}Subscribe{/if}
          </button>
        </form>
      </div>
    {:else}
      <div in:fly="{{ delay: 400, y: 100, duration: 1000 }}">
        <h2 class="text-left mb-8 text-2xl font-bold">
          Thank you for subscribing 💙
        </h2>
      </div>
    {/if}
  </div>
  <div class="py-6 flex-1 flex">
    <div class="md:flex-1"></div>
    <div class="flex flex-wrap md:flex-col items-start md:justify-end">
      {#each social as { href, name, icon }}
        <a
          class="flex my-4 transition-all duration-200 ease-in content-center
          justify-center fill-current text-gray-300 hover:text-teal-200
          hover:border-b-2 border-teal-200 px-2 mx-4"
          {href}
        >
          {@html icon}
          <span class="ml-2">{name}</span>
        </a>
      {/each}
    </div>
  </div>

</div>

<style>
  input {
    @apply px-3 py-2;
    @apply rounded;
    @apply border-0;
    @apply text-gray-700;
  }
</style>
