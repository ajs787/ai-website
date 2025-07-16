<script>
  import { fade } from 'svelte/transition';

  const advisors = [
    {
      name: 'Dr. Richard Martin',
      title: 'Project Advisor',
      //img: '/images/richard-martin.jpg' // replace with real path
    },
    {
      name: 'Dr. Richard Howard',
      title: 'Project Advisor',
      //img: '/images/richard-howard.jpg'
    },
    {
      name: 'Ben Firner',
      title: 'Project Advisor',
      //img: '/images/ben-firner.jpg'
    }
  ];

  const team = [
    {
      name: 'Audrey Shin',
      title: 'CS + CogSci Undergrad \'27',
      //img: '/images/audrey.jpg'
    },
    {
      name: 'Dhruv Daiya',
      title: 'CS + DS Undergrad \'27',
      //img: '/images/dhruv.jpg'
    },
    {
      name: 'Elias Xu',
      title: 'Incoming Cornell Freshman \'29',
      //img: '/images/elias.jpg'
    },
    {
      name: 'Natalie Tang',
      title: 'Lawrenceville School Senior',
      //img: '/images/natalie.jpg'
    },
    {
      name: 'Hannah Hollosi',
      title: 'CS + DS Undergrad \'28',
      //img: '/images/hannah.jpg'
    }
  ];
</script>

<svelte:head>
  <title>Team</title>
  <meta name="description" content="Team" />
</svelte:head>

<section class="team-section" in:fade={{ duration: 300 }}>
  <h1>Team</h1>

  <h2>Project Advisors</h2>
  <div class="grid">
    {#each advisors as person}
      <div class="card">
        <h3>{person.name}</h3>
        <p>{person.title}</p>
      </div>
    {/each}
  </div>

  <h2>Team Members</h2>
  <div class="grid">
    {#each team as person}
      <div class="card">
        <h3>{person.name}</h3>
        <p>{person.title}</p>
      </div>
    {/each}
  </div>
</section>

<style>
	
  .team-section {
    max-width: 1000px;
    margin: 5rem auto;
    padding: 0 2rem;
    text-align: center;
  }
  h1 {
	margin-top: -3rem;
  }

	:global(h1) {
	font-size: 2.8rem;
	font-weight: 800;
	margin-bottom: 3rem;
}

  h2 {
    font-size: 1.6rem;
    margin: 3rem 0 1rem;
    font-weight: 700;
    color: var(--heading-color);
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
    margin-bottom: 4rem;
    justify-items: center;
  }

  @media (max-width: 768px) {
  .grid {
    grid-template-columns: repeat(3, 2fr);
  }
}

  @media (max-width: 500px) {
    .grid {
      grid-template-columns: 2fr;
    }
  }

  .card {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    width: 250px;
    height: 120px;

    background: rgba(93, 94, 101, 0.1);
    border-radius: 10px;
    padding: 1rem;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    text-align: center;

    /* Prevent shrinkage on short text */
    flex-shrink: 0;
  }

  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.08);
  }

  [data-theme='dark'] .card {
    background: rgba(255, 255, 255, 0.05);
    box-shadow: 0 4px 12px rgba(255, 255, 255, 0.05);
  }

  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.08);
  }

  img {
    width: 100%;
    max-width: 120px;
    height: 120px;
    border-radius: 9999px;
    object-fit: cover;
    margin-bottom: 1rem;
  }

  h3 {
    font-size: 1.1rem;
    font-weight: 600;
    margin-bottom: 0.25rem;
    color: var(--heading-color);
  }

  p {
    font-size: 0.9rem;
    margin: 0;
    color: var(--text-color);
  }

</style>
