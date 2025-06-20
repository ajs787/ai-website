<script>
  // Counter import removed
  import DarkModeToggle from './DarkModeToggle.svelte';
</script>

<DarkModeToggle />

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
  <h2>The Mission</h2>
  <p>
    The AI for Behavioural Discovery project aims to understand whether animal behaviour is affected by exposure to EMF radiation using a machine learning and Convolutional Neural Networks(CNNs) approach. We have conducted experiments on cockroaches, bees, and ants so far using AlexNet, achieving positive results with ants. The model was able to successfully classify field states between Positive, Negative and Off based only on behavioural changes of the ants.

  </p>
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
    margin-top: 1rem;
    color: var(--accent-color);
    font-weight: 600;
    text-decoration: none;
  }

  a:hover {
    text-decoration: underline;
  }


</style>
