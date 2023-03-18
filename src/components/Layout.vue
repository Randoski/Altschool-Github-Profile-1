<template>
  <nav class="layout-navs py-[1.7rem] max-md:py-[.4rem] max-md:text-[16px]">
    <p class="layout-link name">{{ this.data }}</p>
    <div class="nav-con">
      <router-link class="layout-link link-extra" to="/">Home</router-link>
      <router-link class="layout-link link-extra" to="/repositories"
        >Repos</router-link
      >
    </div>
      <router-link class="layout-link link-extra" to="/404">404 Page</router-link>
  </nav>
</template>

<script>
export default {
  name: "Layout",
  data() {
    return {
      data: "",
    };
  },
  async created() {
    const res = await fetch("https://api.github.com/users/randoski");
    const data = await res.json();
    this.data = data.name;
  },
};
</script>

<style>
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
  margin: 0.9rem 0;
}

.nav-con {
  display: flex;
  gap: 10px;
}

.layout-navs {
  font-size: 1.2rem;
}

.layout-link {
  list-style: none;
  padding: 0.7em 1.7rem;
  cursor: pointer;
  text-decoration: none;
  color: white;
  border-radius: 10px;
  transition: border-color 0.2s ease-in-out;
}

.link-extra:hover {
  text-decoration: underline;
}

.name {
  padding-left: 0;
  font-weight: 600;
}

.router-link- {
  border: 1px solid transparent;
}

.router-link-active {
  border: 1px solid white;
}

@media (max-width: 801px) {
  .layout-link {
    padding: 0 0.6rem;
  }
  .name {
    display: none;
  }
}
</style>
