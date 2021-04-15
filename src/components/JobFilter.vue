<template>
  <div class="wrapper">
    <transition-group name="filterItem" tag="ul">
      <li v-for="filter in filterOption" :key="filter">
        <span>
          {{ filter }}
        </span>
        <button @click="removeFilter">
          <img src="../assets/icon-remove.svg" alt="X" />
        </button>
      </li>
    </transition-group>
    <button @click="clearFilter" class="btn-clear">Clear</button>
  </div>
</template>
<script>
export default {
  inject: ["filterOption"],
  methods: {
    clearFilter() {
      this.filterOption.length = 0;
    },
    removeFilter(el) {
      const filterToDelete =
        el.target.parentElement.parentElement.children[0].textContent;
      const deletingFilterIndex = this.filterOption.indexOf(filterToDelete);
      this.filterOption.splice(deletingFilterIndex, 1);
    },
  },
};
</script>
<style scoped>
.wrapper {
  border-radius: 5px;
  box-shadow: 8px 8px 15px rgba(0, 0, 0, 0.1);
  width: 70%;
  padding: 25px;
  background-color: #fff;
  position: absolute;
  top: 10vh;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  justify-content: space-between;
}
ul {
  list-style: none;
  display: flex;

  flex-wrap: wrap;
}
li {
  margin: 1px 5px;
  color: var(--DesaturatedDarkCyan);
  background-color: var(--LightGrayishCyanFilterTablets);
  padding: 2px 5px;
  display: flex;
  align-items: center;
}
li > span {
  padding: 0 5px;
  user-select: none;
}
li > button {
  background-color: var(--DesaturatedDarkCyan);
  border: none;
  padding: 4px;
  cursor: pointer;
  outline: none;
  display: flex;
  align-items: center;
}
.filterItem-enter-active {
  animation: fade 0.1s ease-in;
}
.btn-clear {
  color: var(--DesaturatedDarkCyan);
  border: 2px transparent solid;

  outline: none;
  background: transparent;
  font-size: 1.3rem;
  padding: 2px 5px;
  cursor: pointer;
  border-radius: 5px;
  transition: all 0.2s ease;
}
.btn-clear:hover {
  border: 2px var(--DesaturatedDarkCyan) solid;
}
</style>
