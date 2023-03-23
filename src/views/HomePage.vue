<template>
  <div>
    <Layout />
    <div class="mt-[3rem] max-md:mt-[10rem] hero-con">
      <div class="con1">
        <!-- Hero text -->
        <div>
          <h1 class="front-page-heading tracking-tighter">Frontend</h1>
          <h1 class="front-page-heading tracking-tighter">Developer</h1>
          <p class="temp">{{ this.bio }}</p>
          <router-link to="/repositories"
            ><Btn
              className="bg-slate-700 hover:bg-black"
              link="/repositories"
              text="My Repositories"
          /></router-link>
        </div>

        <!-- Image -->
        <div class="img-and-bg-container">
          <img :src="this.displayImage" alt="User image" class="user-img" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Layout from "../components/Layout.vue";
import Paragraph from "@/components/typography/Paragraph.vue";
import SmallText from "@/components/typography/SmallText.vue";
import Btn from "@/components/Button.vue";
// import SmallTextVue
import Link from "../components/Links.vue";

export default {
  name: "HomePage",
  components: {
    Layout,
    Paragraph,
    Link,
    SmallText,
    Btn,
  },

  data() {
    return {
      displayImage: "",
      bio: "",
    };
  },

  methods: {
    async github() {
      const response = await fetch("https://api.github.com/users/Randoski");
      const data = await response.json();
      this.displayImage = data.avatar_url;
      this.bio = data.bio;
      console.log(this.bio);
    },
  },

  mounted() {
    this.github();
  },
};
</script>

<style>
.hero-con {
  display: grid;
  grid-template-columns: 1fr 0.3fr;
  gap: 3rem;
  align-items: center;
}

.temp {
  color: white;
}

.front-page-heading {
  font-size: 9vw;
  font-weight: 500;
  line-height: 170px;
  color: white;
}

.user-img {
  height: auto;
  width: 100%;
  margin-left: 10rem;
}

.con1 {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 4em;
}

@media (max-width: 801px) {
  .front-page-heading {
    font-size: 16vw;
    line-height: 13vw;
  }
  .socials {
    display: none;
  }

  .con1 {
    flex-direction: column;
    margin-left: 0;
  }

  .user-img {
    margin-left: 0;
    margin-top: 24px;
  }
}
</style>
