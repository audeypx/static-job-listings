<template>
  <body>
    <header class="header">
      <div id="search-field">
        <input
          type="text"
          id="ItemList"
          v-model="searchQuery"
          placeholder="Search..."
          class="tw-w-full focus:tw-outline-none"
          @keyup.prevent="filterJobs"
        />
      </div>
      <span class="close">Clear</span>
    </header>
    <div class="container">
      <ul id="items" class="main-content">
        <li v-for="(job, i) in displayJobs" :key="i" class="">
          <div class="card featured">
            <img src="images/photosnap.svg" alt="photosnap" />
            <img
        v-bind:src="picture"
        :alt="firstName"
        :class="gender"
      />
            <div class="col-left">
              <h3 class="company">
                {{ job.company_name }}
              </h3>
              <button class="new-btn" v-if="job.new">NEW!</button>
              <button class="feature-btn" v-if="job.featured">FEATURED</button>
              <h2 class="job-title">
                <p>{{ job.jobTitle }}</p>
              </h2>
              <div class="job-details">
                <p>
                  {{ job.date }}<span> &bull;</span>{{ job.period
                  }}<span>&bull;</span>{{ job.location }}
                </p>
              </div>
            </div>

            <div class="col-right">
              <div class="skills">
                <div class="choose role">{{ job.role }}</div>
                <div class="choose level">{{ job.level }}</div>
                <div
                  class="choose languages"
                  v-for="(x, y) in job.languages"
                  :key="y"
                >
                  {{ x }}
                </div>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
    <!-- <div class="container">
      <div class="main-content">
        <div class="card featured">
          <img src="images/photosnap.svg" alt="photosnap" />
          <div class="col-left">
            <h3 class="company">Photosnap</h3>
            <button class="new-btn">New!</button>
            <button class="feature-btn">Featured</button>
            <h2 class="job-title">Senior Frontend Developer</h2>
            <div class="job-details">
              <p>
                1d ago<span> &bull;</span>Full Time<span>&bull;</span>USA only
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Frontend</div>
              <div class="choose level">Senior</div>
              <div class="choose languages">HTML</div>
              <div class="choose languages">CSS</div>
              <div class="choose languages">JavaScript</div>
            </div>
          </div>
        </div>
        <div class="card featured">
          <img src="images/manage.svg" alt="manage" />
          <div class="col-left">
            <h3 class="company">Manage</h3>
            <button class="new-btn">New!</button>
            <button class="feature-btn">Featured</button>
            <h2 class="job-title">Fullstack Developer</h2>
            <div class="job-details">
              <p>
                1d ago<span> &bull;</span>Part Time<span>&bull;</span>Remote
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Fullstack</div>
              <div class="choose level">Midweight</div>
              <div class="choose languages">Python</div>
              <div class="choose tools">React</div>
            </div>
          </div>
        </div>
        <div class="card">
          <img src="images/account.svg" alt="account" />
          <div class="col-left">
            <h3 class="company">Account</h3>
            <button class="new-btn">New!</button>

            <h2 class="job-title">Junior Frontend Developer</h2>
            <div class="job-details">
              <p>
                2d ago<span> &bull;</span>Part Time<span>&bull;</span>USA only
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Frontend</div>
              <div class="choose level">Junior</div>
              <div class="choose languages">JavaScript</div>
              <div class="choose tools">React</div>
              <div class="choose tools">Sass</div>
            </div>
          </div>
        </div>
        <div class="card">
          <img src="images/myhome.svg" alt="myhome" />
          <div class="col-left">
            <h3 class="company">MyHome</h3>
            <button class="new-btn">New!</button>

            <h2 class="job-title">Junior Frontend Developer</h2>
            <div class="job-details">
              <p>
                5d ago<span> &bull;</span>Contract<span>&bull;</span>USA only
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Frontend</div>
              <div class="choose level">Junior</div>
              <div class="choose languages">CSS</div>
              <div class="choose languages">JavaScript</div>
            </div>
          </div>
        </div>
        <div class="card">
          <img src="images/loop-studios.svg" alt="loopstudio" />
          <div class="col-left">
            <h3 class="company">Loop Studios</h3>

            <h2 class="job-title">Software Engineer</h2>
            <div class="job-details">
              <p>
                1w ago<span> &bull;</span>Full Time<span>&bull;</span>Worldwide
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Fullstack</div>
              <div class="choose level">Midweight</div>

              <div class="choose languages">JavaScript</div>
              <div class="choose tools">Ruby</div>
              <div class="choose tools">Sass</div>
            </div>
          </div>
        </div>
        <div class="card">
          <img src="images/faceit.svg" alt="faceit" />
          <div class="col-left">
            <h3 class="company">FaceIt</h3>

            <h2 class="job-title">Junior Backend Developer</h2>
            <div class="job-details">
              <p>
                2w ago<span> &bull;</span>Full Time<span>&bull;</span>UK only
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Backend</div>
              <div class="choose level">Junior</div>

              <div class="choose languages">Ruby</div>
              <div class="choose tools">RoR</div>
            </div>
          </div>
        </div>
        <div class="card">
          <img src="images/shortly.svg" alt="shortly" />
          <div class="col-left">
            <h3 class="company">Shortly</h3>

            <h2 class="job-title">Junior Developer</h2>
            <div class="job-details">
              <p>
                2w ago<span> &bull;</span>Full Time<span>&bull;</span>Worldwide
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Frontend</div>
              <div class="choose level">Junior</div>

              <div class="choose languages">HTML</div>
              <div class="choose languages">JavaScript</div>
              <div class="choose tools">Sass</div>
            </div>
          </div>
        </div>
        <div class="card">
          <img src="images/insure.svg" alt="insure" />
          <div class="col-left">
            <h3 class="company">Insure</h3>

            <h2 class="job-title">Junior Frontend Developer</h2>
            <div class="job-details">
              <p>
                2w ago<span> &bull;</span>Full Time<span>&bull;</span>USA only
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Frontend</div>
              <div class="choose level">Junior</div>

              <div class="choose languages">JavaScript</div>
              <div class="choose tools">Vue</div>
              <div class="choose tools">Sass</div>
            </div>
          </div>
        </div>
        <div class="card">
          <img src="images/eyecam-co.svg" alt="Eyecam Co." />
          <div class="col-left">
            <h3 class="company">Eyecam Co.</h3>

            <h2 class="job-title">Full Stack Engineer</h2>
            <div class="job-details">
              <p>
                3w ago<span> &bull;</span>Full Time<span>&bull;</span>Worldwide
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Fullstack</div>
              <div class="choose level">Midweight</div>

              <div class="choose languages">JavaScript</div>
              <div class="choose languages">Python</div>
              <div class="choose tools">Django</div>
            </div>
          </div>
        </div>
        <div class="card">
          <img
            src="images/the-air-filter-company.svg"
            alt="The Air Filter Company"
          />
          <div class="col-left">
            <h3 class="company">The Air Filter Company</h3>

            <h2 class="job-title">Front-end Dev</h2>
            <div class="job-details">
              <p>
                1mo ago<span> &bull;</span>Part Time<span>&bull;</span>Worldwide
              </p>
            </div>
          </div>
          <div class="col-right">
            <div class="skills">
              <div class="choose role">Frontend</div>
              <div class="choose level">Junior</div>

              <div class="choose languages">JavaScript</div>
              <div class="choose languages">React</div>
              <div class="choose tools">Sass</div>
            </div>
          </div>
        </div>
      </div>
    </div> -->

    <div class="attribution">
      Challenge by
      <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
        >Frontend Mentor</a
      >. Coded by <a href="">audrey</a>.
    </div>
  </body>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
      jobs: [
        {
          company_name: "Photosnap",
          jobTitle: "Senior Frontend Developer",
          new: true,
          featured: true,
          location: "USA only",
          date: "1d ago",
          period: "Full Time",
          role: "Frontend",
          level: "Senior",
          languages: ["HTML", "CSS", "Javascript"],
        },
        {
          company_name: "Manage",
          jobTitle: "FullStack Developer",
          new: true,
          featured: true,
          location: "Remote",
          date: "1d ago",
          period: "Part Time",
          role: "Fullstack",
          level: "Midweight",
          languages: ["Python", "React"],
        },
        {
          company_name: "Account",
          jobTitle: "Junior Frontend Developer",
          new: true,
          featured: false,
          location: "USA only",
          date: "2d ago",
          period: "Part Time",
          role: "Frontend",
          level: "Junior",
          languages: ["Javascript", "React", "Sass"],
        },
        {
          company_name: "MyHome",
          jobTitle: "Junior Frontend Developer",
          new: true,
          featured: false,
          location: "USA only",
          date: "5d ago",
          period: "Contract",
          role: "Frontend",
          level: "Junior",
          languages: ["CSS", "Javascript"],
        },
        {
          company_name: "Shortly",
          jobTitle: "Junior Developer",
          new: false,
          featured: false,
          location: "Worldwide",
          date: "2w ago",
          period: "Full Time",
          role: "Frontend",
          level: "Junior",
          languages: ["HTML", "Javascript", "Sass"],
        },
        {
          company_name: "Insure",
          jobTitle: "Junior Frontend Developer",
          new: false,
          featured: false,
          location: "USA only",
          date: "2w ago",
          period: "Full Time",
          role: "Frontend",
          level: "Junior",
          languages: ["Javascript", "Vue", "Sass"],
        },
        {
          company_name: "The Air Filter Company",
          jobTitle: "Front-end Dev",
          new: true,
          featured: false,
          location: "Worldwide",
          date: "1mo ago",
          period: "Part Time",
          role: "Frontend",
          level: "Junior",
          languages: ["Javascript", "React", "Sass"],
        },
      ],
      displayJobs: [],
    };
  },
  methods: {
    itemAdd() {},
    filterJobs() {
      if (this.searchQuery) {
        this.displayJobs = this.jobs.filter(
          (opt) =>
            opt.jobTitle
              .toLowerCase()
              .includes(this.searchQuery.toLowerCase()) ||
            opt.companyTitle
              .toLowerCase()
              .includes(this.searchQuery.toLowerCase()) ||
            opt.location.toLowerCase().includes(this.searchQuery.toLowerCase())
        );
        return;
      }
      this.displayJobs = this.jobs;
    },
    
  },
  mounted() {
    this.displayJobs = this.jobs;
    this.fetchJobs();
  },
};
</script>

 <style>
.attribution {
  font-size: 11px;
  text-align: center;
}
.attribution a {
  color: hsl(228, 45%, 44%);
}

template {
  height: 100%;
  width: 100%;
  box-sizing: border-box;
  font-size: 100%;
}
body {
  background: hsl(180, 52%, 96%);
  font-family: "Spartan", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-size: 15px;
}
header {
  background-color: hsl(180, 29%, 50%);
  /* background-image: url("images/bg-header-mobile.svg"); */
  background-size: cover;
  background-repeat: no-repeat;
  position: relative;
  height: 12em;
}
.container {
  padding-top: 5em;
}
.main-content {
  width: 90%;
  margin: auto;
}
h2 {
  color: hsl(180, 14%, 20%);
  font-size: 1.1rem;
  margin-top: 0;
  cursor: pointer;
  transition: all 300ms ease-in-out;
}
h2:hover {
  color: hsl(180, 29%, 50%);
}
h3 {
  color: hsl(180, 29%, 50%);
  font-size: 1rem;
}

/*header-part*/

#search-field {
  background: hsl(180, 31%, 95%);
  box-shadow: 0px 5px 20px hsl(180, 29%, 50%);
  position: absolute;
  bottom: -2rem;
  left: 5%;
  height: 5.5em;
  width: 90%;
  padding: 0.5rem;
  border-radius: 5px;
  display: none;
  animation-duration: 3s;
}
.close {
  color: hsl(180, 8%, 52%);
  position: absolute;
  bottom: 2%;
  right: 10%;
  display: none;
  animation-duration: 3s;
  cursor: pointer;
}
.close:hover {
  color: hsl(180, 29%, 50%);
  text-decoration: underline;
}

.item {
  color: hsl(180, 29%, 50%);
  background-color: hsla(180, 28.6%, 50%, 0.12);
  font-size: 0.8rem;
  font-weight: 700;
  display: inline-block;
  position: relative;
  margin-right: 1rem;
  margin-bottom: 1rem;
  padding: 0.6rem 0.8rem;
  padding-right: 2.2rem;
  border-radius: 10px;
  cursor: pointer;
}

.item:after {
  content: "X";
  position: absolute;
  right: 0;
  bottom: 0;
  background-color: hsl(180, 29%, 50%);
  color: white;
  padding: 10px;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
  font-weight: 700;
}
.item:hover::after {
  background-color: hsl(180, 14%, 20%);
}
/*cards*/

.card {
  background-color: hsl(180, 31%, 95%);
  box-shadow: 0px 5px 20px hsl(180, 29%, 50%);
  padding: 1.5rem;
  border-radius: 10px;
  margin-bottom: 3rem;
}
.featured {
  border-left: 4px solid hsl(180, 29%, 50%);
}
img {
  display: block;
  margin-top: -4rem;
}
.company {
  display: inline-block;
}
.new-btn {
  color: hsl(180, 31%, 95%);
  background-color: hsl(180, 29%, 50%);
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
  padding: 0.3rem 0.8rem;
  margin-left: 0.5rem;
  margin-right: 0.5rem;
  border: none;
  border-radius: 1rem;
}
.feature-btn {
  color: hsl(180, 31%, 95%);
  background-color: hsl(180, 14%, 20%);
  font-size: 0.7rem;
  font-weight: 700;
  text-transform: uppercase;
  padding: 0.3rem 0.8rem;
  border: none;
  border-radius: 1rem;
}
.job-details {
  border-bottom: 1px solid hsl(180, 8%, 52%);
}
.job-details p {
  color: hsl(180, 8%, 52%);
  font-size: 0.9rem;
  font-weight: 500;
}
.job-details > p > span {
  padding-left: 0.5em;
  padding-right: 0.5em;
}

.skills {
  margin-top: 1rem;
}
.role,
.level,
.languages,
.tools {
  color: hsl(180, 29%, 50%);
  background-color: hsla(180, 28.6%, 50%, 0.12);
  font-size: 0.8rem;
  font-weight: 700;
  display: inline-block;
  margin-right: 1rem;
  margin-bottom: 1rem;
  padding: 0.6rem 0.7rem;
  border-radius: 10px;
  cursor: pointer;
  transition: all 300ms ease-in-out;
}
.role:hover,
.level:hover,
.languages:hover,
.tools:hover {
  color: hsl(180, 31%, 95%);
  background-color: hsl(180, 29%, 50%);
}

.filtered {
  display: none;
}

@media (min-width: 1000px) {
  .col-left {
    flex-grow: 2;
    margin-left: 2rem;
  }
  .card {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  img {
    display: inline-block;
    margin-top: 0;
  }
  .job-details {
    border: none;
  }
  #search-field {
    height: 4rem;
  }
  .filtered {
    display: none;
  }
}
</style>
