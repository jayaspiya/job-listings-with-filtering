<template>
  <li :class="{ 'featured-list': isFeatured }">
    <div class="company-detail">
      <img :src="logoLocation" />
      <div class="company-bio">
        <div class="title">
          <div class="company-name">
            {{ job.company }}
          </div>
          <div class="highlight">
            <span class="highlight--new" v-if="job.new">
              NEW!
            </span>
            <span class="highlight--featured" v-if="job.featured">
              FEATURED
            </span>
          </div>
        </div>

        <div class="company-position">
          {{ job.position }}
        </div>
        <div class="more-info">
          <div class="last-online">
            {{ job.postedAt }}
          </div>
          <div class="dot"></div>
          <div class="contract">
            {{ job.contract }}
          </div>
          <div class="dot"></div>
          <div class="location">
            {{ job.location }}
          </div>
        </div>
      </div>
    </div>
    <div class="skill-list">
      <div
        class="skill"
        v-for="skill in skills"
        :key="skill"
        @click="addFilter"
      >
        {{ skill }}
      </div>
    </div>
  </li>
</template>

<script>
export default {
  props: ["job"],
  computed: {
    logoLocation() {
      const url = require("@/assets/images" + this.job.logo);
      return url;
    },
    isFeatured() {
      return this.job.new && this.job.featured;
    },
    skills() {
      const skills = [
        this.job.role,
        this.job.level,
        ...this.job.languages,
        ...this.job.tools,
      ];
      return skills;
    },
  },
  methods: {
    addFilter(el) {
      if (!this.filterOption.includes(el.target.textContent)) {
        this.filterOption.push(el.target.textContent);
      }
    },
  },
  inject: ["filterOption"],
};
</script>

<style scoped>
li {
  border-radius: 5px;
  box-shadow: 8px 8px 15px rgba(0, 0, 0, 0.1);
  width: 70%;
  margin: 15px auto;
  padding: 30px;
  background-color: #fff;
  display: flex;
  justify-content: space-between;
}
img {
  width: 80px;
  height: 80px;
  margin: auto;
  margin-right: 15px;
}
.company-detail {
  display: flex;
}

.company-name {
  color: var(--DesaturatedDarkCyan);
  font-weight: 700;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 0.9em;
}

.company-position {
  margin: 10px 0;
  color: var(--VeryDarkGrayishCyan);
  text-align: center;
  font-weight: 700;
}
.dot {
  height: 4px;
  width: 4px;
  background-color: var(--DarkGrayishCyan);
  border-radius: 50%;
  margin: auto;
}
.more-info {
  display: flex;
  justify-content: space-between;
  font-size: 0.9em;
  color: var(--DarkGrayishCyan);
}
.more-info > div {
  margin: auto 10px;
}
.skill-list {
  display: flex;
  align-items: center;
  justify-content: center;
}
.skill {
  font-size: 0.9em;
  margin: 6px;
  padding: 5px;
  border-radius: 6px;
  color: var(--DesaturatedDarkCyan);
  background-color: var(--LightGrayishCyanFilterTablets);
  cursor: pointer;
  transition: all 0.1s ease-in;
}
.skill:hover {
  background-color: var(--DesaturatedDarkCyan);
  color: var(--LightGrayishCyanFilterTablets);
}
.featured-list {
  border-left: 6px solid var(--DesaturatedDarkCyan);
}

.highlight {
  margin: 0 10px;
  font-size: 0.7rem;
  color: #fff;
  display: flex;
}

.highlight span {
  margin: 5px;
  padding: 4px 5px;
  border-radius: 30px;
  cursor: pointer;
  font-weight: 700;
}

.highlight--new {
  background-color: var(--DesaturatedDarkCyan);
}
.highlight--featured {
  background-color: var(--VeryDarkGrayishCyan);
}

.title {
  display: flex;
  justify-content: center;
}

@media screen and (max-width: 1150px) {
  li {
    display: flex;
    flex-direction: column;
  }

  .company-detail {
    display: flex;
    text-align: center;
    flex-direction: column;
  }

  .company-bio {
    padding: 20px;
  }

  .skill-list {
    display: flex;
    flex-wrap: wrap;
  }
  img {
    margin: auto;
  }
  .more-info {
    justify-content: center;
  }
}
</style>
