<script>
  import { onMount } from 'svelte';

  let isDark = false;
  let rotateLight = false;
  let rotateDark = false;

  onMount(() => {
    const savedTheme = localStorage.getItem("theme");
    const systemPrefersDark = window.matchMedia("(prefers-color-scheme: dark)").matches;
    isDark = savedTheme === "dark" || (!savedTheme && systemPrefersDark);
    document.documentElement.setAttribute("data-theme", isDark ? "dark" : "light");
  });

  function toggleTheme() {
    isDark = !isDark;
    document.documentElement.classList.add("theme-transition");

    document.documentElement.setAttribute("data-theme", isDark ? "dark" : "light");
    localStorage.setItem("theme", isDark ? "dark" : "light");

    // Reset rotation state to re-trigger animation
    rotateLight = false;
    rotateDark = false;

    // Trigger next animation frame so the reset takes effect
    requestAnimationFrame(() => {
      rotateLight = true;
      rotateDark = true;
    });

    setTimeout(() => {
      document.documentElement.classList.remove("theme-transition");
    }, 800);
  }
</script>
  

<style>
  .switch {
    display: flex;
    align-items: center;
    position: relative;
    width: 75px;
    height: 40px;
    border: 2px solid white;
    border-radius: 9999px;
    cursor: pointer;
    padding: 4px;
    background-color: transparent;
  }

  .switch__icon {
    width: 20px;
    height: 20px;
    color: white;
    transition: color 0.6s ease, fill 0.6s ease, transform 0.6s ease;
  }

  .switch__inner {
    position: absolute;
    width: 30px;
    height: 30px;
    background-color: #2dd4bf;
    border-radius: 50%;
    top: 8px;
    left: 9px;
    transition: left 0.2s ease-in-out;
  }

  .dark .switch__inner {
    left: calc(100% - 39px);
  }

  .switch__inner-icons {
    display: flex;
    justify-content: space-between;
    width: 100%;
    z-index: 1;
    padding: 0 10px;
  }

  .switch__sr {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
  }
  .rotate {
    animation: spin 0.6s ease;
  }
  .rotate-reverse {
  animation: spin-reverse 0.6s ease;
  }

  @keyframes spin {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
  }

  @keyframes spin-reverse {
  from { transform: rotate(0deg); }
  to { transform: rotate(-360deg); }
  }

</style>

<svg style="display: none">
  <symbol id="icon-light" viewBox="0 0 24 24">
    <g stroke="currentColor" stroke-width="2" stroke-linecap="round">
      <line x1="12" y1="17" x2="12" y2="20" transform="rotate(0,12,12)" />
      <line x1="12" y1="17" x2="12" y2="20" transform="rotate(45,12,12)" />
      <line x1="12" y1="17" x2="12" y2="20" transform="rotate(90,12,12)" />
      <line x1="12" y1="17" x2="12" y2="20" transform="rotate(135,12,12)" />
      <line x1="12" y1="17" x2="12" y2="20" transform="rotate(180,12,12)" />
      <line x1="12" y1="17" x2="12" y2="20" transform="rotate(225,12,12)" />
      <line x1="12" y1="17" x2="12" y2="20" transform="rotate(270,12,12)" />
      <line x1="12" y1="17" x2="12" y2="20" transform="rotate(315,12,12)" />
    </g>
    <circle fill="currentColor" cx="12" cy="12" r="5" />
  </symbol>
  <symbol id="icon-dark" viewBox="0 0 24 24">
    <path fill="currentColor" d="M15.1,14.9c-3-0.5-5.5-3-6-6C8.8,7.1,9.1,5.4,9.9,4c0.4-0.8-0.4-1.7-1.2-1.4C4.6,4,1.8,7.9,2,12.5c0.2,5.1,4.4,9.3,9.5,9.5c4.5,0.2,8.5-2.6,9.9-6.6c0.3-0.8-0.6-1.7-1.4-1.2C18.6,14.9,16.9,15.2,15.1,14.9z" />
  </symbol>
</svg>

<div class="switch" on:click={toggleTheme} class:dark={isDark}>
  <span class="switch__inner"></span>
  <span class="switch__inner-icons">
    <svg
      class="switch__icon"
      class:rotate-reverse={rotateLight}
      on:animationend={() => (rotateLight = false)}>
      <use href="#icon-light" />
    </svg>

    <svg
      class="switch__icon"
      class:rotate={rotateDark}
      on:animationend={() => (rotateDark = false)}>
      <use href="#icon-dark" />
    </svg>
  </span>
  <span class="switch__sr">Toggle Dark Mode</span>
</div>

