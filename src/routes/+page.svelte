<svelte:head>
  <title>Home</title>
  <meta name="description" content="AI for Behavioral Discovery project site" />
</svelte:head>

<section>
  <h1 class="main-title">
    AI for Behavioral Discovery
  </h1>

  <p class="project-blurb">
    This ongoing project uses machine learning and CNNs to uncover how EMF radiation may impact animal behavior. Since 2019, we have been turning complex behavioral patterns into actionable insights through AI.  </p>
</section>

<!-- What We Do Section -->
<section class="what-we-do">

  <a href="/about">Click here to learn more --></a>

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

  .description{
    
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
	margin-top: 3rem;
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
    font-size: 1.5rem;
    margin-top: 1rem;
    margin-bottom: 5rem;
    color: var(--accent-color);
    font-weight: 600;
    text-decoration: none;
  }

  a:hover {
    text-decoration: underline;
  }


</style>
