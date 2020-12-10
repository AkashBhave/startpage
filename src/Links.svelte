<script lang="ts">
  type Link = {
    name: string;
    url: string;
  };

  let links: { [category: string]: Link[] } = {
    Personal: [
      {
        name: "Mail",
        url: "https://mail.google.com/mail/u/0",
      },
      {
        name: "GitHub",
        url: "https://www.github.com",
      },
      {
        name: "Strava",
        url: "https://www.strava.com",
      },
    ],
    School: [
      {
        name: "Mail",
        url: "https://mail.google.com/mail/u/1",
      },
      {
        name: "Blackboard",
        url: "https://fcps.blackboard.com",
      },
      {
        name: "Classroom",
        url: "https://classroom.google.com/u/1",
      },
      {
        name: "Grades",
        url: "https://sisstudent.fcps.edu",
      },
    ],
  };
</script>

<style>
  section {
    display: grid;
    grid-auto-flow: column;
    grid-gap: 3em;
  }

  .category {
    margin: 0 0 20px;
    font-size: 1em;
  }

  .link {
    font-size: 0.6em;
    opacity: 0.8;
    margin-bottom: 10px;
    display: block;
    display: flex;
    align-items: center;
  }
  .arrow {
    opacity: 0;
    display: inline;
    margin-left: 10px;
    transition: 0.5s all ease;
    fill: #183675;
  }
  .link:hover,
  .link:hover .arrow {
    opacity: 1;
  }
</style>

<section>
  {#each Object.keys(links) as category}
    <div>
      <h3 class="category">{category}</h3>
      <div>
        {#each links[category] as link}
          <a class="link" href={link.url}>
            <span>{link.name}</span>
            <svg
              class="arrow"
              width="24"
              height="24"
              xmlns="http://www.w3.org/2000/svg"
              fill-rule="evenodd"
              clip-rule="evenodd"><path
                d="M21.883 12l-7.527 6.235.644.765 9-7.521-9-7.479-.645.764 7.529 6.236h-21.884v1h21.883z" />
            </svg>
          </a>
        {/each}
      </div>
    </div>
  {/each}
</section>
