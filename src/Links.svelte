<script lang="ts">
  type Link = {
    name: string;
    url: string;
    color: string;
  };

  let links: { [category: string]: Link[] } = {
    Personal: [
      {
        name: "Mail",
        url: "https://mail.google.com/mail/u/0",
        color: "#EA4335",
      },
      {
        name: "GitHub",
        url: "https://www.github.com",
        color: "#323131",
      },
      {
        name: "Strava",
        url: "https://www.strava.com",
        color: "#FE5E00",
      },
      {
        name: "Facebook",
        url: "https://www.facebook.com",
        color: "#4064AC",
      },
      {
        name: "Reddit",
        url: "https://www.reddit.com",
        color: "#EC4E14",
      },
    ],
    School: [
      {
        name: "Mail",
        url: "https://mail.google.com/mail/u/1",
        color: "#EA4335",
      },
      {
        name: "Blackboard",
        url: "https://fcps.blackboard.com",
        color: "#B38432",
      },
      {
        name: "Classroom",
        url: "https://classroom.google.com/u/1",
        color: "#3E9958",
      },
      {
        name: "Grades",
        url: "https://sisstudent.fcps.edu",
        color: "#642068",
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
	@media screen and (max-height: 650px) {
			.category {
					margin-bottom: 10px;
					}
	}

  .link {
    font-size: 0.6em;
    opacity: 0.8;
    margin-bottom: 10px;
    display: block;
    display: flex;
    align-items: center;
  }
	@media screen and (max-height: 650px) {
			.link {
					margin-bottom: 3px;
			}
	}
  .arrow {
    opacity: 0;
    display: inline;
    margin-left: 10px;
    transition: 0.3s all ease-out;
    fill: #183675;
  }
  .link:hover,
  .link:hover .arrow {
    opacity: 1;
  }

  .color {
    height: 10px;
    width: 10px;
    margin-right: 10px;
  }
</style>

<section>
  {#each Object.keys(links) as category}
    <div>
      <h3 class="category">{category}</h3>
      <div>
        {#each links[category] as link}
          <a class="link" href={link.url}>
            <div class="color" style="background-color: {link.color};" />
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
