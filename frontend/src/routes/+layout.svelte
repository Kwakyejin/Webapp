<script>
  import "../app.postcss";
  import { Navbar, NavBrand, NavLi, NavUl, NavHamburger } from 'flowbite-svelte'
  import { page } from "$app/stores";

</script>

<header>

  <Navbar let:hidden let:toggle>
    <NavBrand href="/">
      <img
        src="https://flowbite.com/docs/images/logo.svg"
        class="mr-3 h-6 sm:h-9"
        alt="Flowbite Logo"
      />
      <span class="self-center whitespace-nowrap text-xl font-semibold dark:text-white">
        계산기
      </span>
    </NavBrand>
    <NavHamburger on:click={toggle} />
    <NavUl {hidden}>

      <NavLi href="/" active={ $page.url.pathname ==='/' ? true: false}>Home</NavLi>
      <NavLi href="/about" active={ $page.url.pathname ==='/about' ? true: false}>About</NavLi>
    </NavUl>
  </Navbar>


</header>
<main class="px-2 sm:px-4">
  <div class="container mx-auto">
  <slot />
</div>
</main>
<footer>
  <hr/>
  <div class="text-center text-gray-500 text-sm py-3">
    Made with ❤️ by <a href="https://flowbite.com" class="text-blue-500">Flowbite</a>

</footer>
