<template>
  <li>
    <div class="company-detail">
      <img :src="job.logo" alt="" />
      <div class="company-bio">
        <div class="company-name">
          {{ job.company }}
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
      <div class="skill">
        {{ job.role }}
      </div>
      <div class="skill">
        {{ job.level }}
      </div>
      <div class="skill" v-for="skill in job.languages" :key="skill">
        {{ skill }}
      </div>
      <div class="skill" v-for="tool in job.tools" :key="tool">
        {{ tool }}
      </div>
    </div>
  </li>
</template>

<script>
export default {
  props: ["job"],
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
  padding: 3px;
  border-radius: 6px;
  color: var(--DesaturatedDarkCyan);
  background-color: var(--LightGrayishCyanFilterTablets);
  cursor: pointer;
}
</style>
