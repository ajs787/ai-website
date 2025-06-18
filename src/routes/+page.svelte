<script>
  // Counter import removed
</script>

<svelte:head>
  <title>Home</title>
  <meta name="description" content="AI for Behavioral Discovery project site" />
</svelte:head>

<section>
  <h1 class="main-title">
    AI for Behavioral Discovery
  </h1>

  <p class="project-blurb">
    Launched in 2019, this ongoing 6-year project explores how artificial intelligence can be used to analyze and uncover patterns in behavioral data. From academic theory to applied insight, we continue to push the frontier of AI-driven discovery.
  </p>
</section>

<!-- What We Do Section -->
<section class="what-we-do">
  <h2>What We Do</h2>
  <p>
    Our team builds intelligent systems that can identify, track, and predict complex behavioral trends across time. From lab studies to real-world environments, our models adapt to dynamic, messy human data.
  </p>
</section>

<!-- Contact/Join Section -->
<section class="get-involved">
  <h2>Get Involved</h2>
  <p>Want to collaborate, contribute, or learn more? Reach out to our team or explore the open-source tools we’ve built.</p>
  <a href="/about">Meet the team →</a>
</section>


<style>
  section {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 4rem 2rem;
    max-width: 800px;
    margin: 0 auto;
    text-align: center;
  }


  .main-title {
    font-size: 4.5rem;
    font-weight: 800;
    font-family: 'Inter', 'Segoe UI', Roboto, sans-serif;
    color: var(--heading-color);
    margin-bottom: 1.5rem;
  }

  .project-blurb {
    font-size: 1.2rem;
    line-height: 1.8;
    color: var(--text-color);
    font-family: 'Open Sans', sans-serif;
  }

  .what-we-do,
  .get-involved {
    background-color: var(--tertiary-color);
    border-radius: 12px;
    margin-top: 20rem;
    padding: 2rem;
  }

  h2 {
    font-size: 2rem;
    margin-bottom: 1rem;
    color: var(--heading-color);
  }

  a {
    margin-top: 1rem;
    color: var(--accent-color);
    font-weight: 600;
    text-decoration: none;
  }

  a:hover {
    text-decoration: underline;
  }


</style>
