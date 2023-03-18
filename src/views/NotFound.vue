<template>
  <Layout />
  <div class="grid grid-cols-[1fr,1fr] max-md:block error-page">
    <div class="img-container">
      <img src="../assets/404.svg" alt="404" class="img-404 " />
    </div>
    <div class="link-container">
      <!-- <Btn class="text-extra" className="bg-slate-300 text-slate-500" text="Page not found" /> -->
      <h1 class="text-extra text-extra1 w-[80%] max-md:w-full text-[1.4rem]">Oops, Page not Found</h1>
      <Paragraph class="text-extra"  className="w-[80%] max-md:w-full text-[1.4rem]" text="The page you are trying to access is not available or does not exist, please check back." />
      <RouterLink to="/" ><Btn class="des" className="hover:bg-gray-500 max-md:mt-[2.1rem] mt-[.9rem]" text="Return to Homepage" /></RouterLink>
    </div>
  </div>
</template>
<script>
import Layout from "../components/Layout.vue";
import Heading from "@/components/typography/Heading.vue";
import Btn from "@/components/Button.vue";
import Paragraph from "@/components/typography/Paragraph.vue";


export default {
  name: "NotFound",

  components: {
    Layout, Heading, Paragraph, Btn
  },
};
</script>
<style>
.error-page {
  gap: 3rem;
  align-items: center;
}

.img-404 {
  width: 100%;
}

.text-extra {
  color: white;
}

.text-extra1 {
  padding-bottom: 8px;
  font-weight: 900;
}

.des {
  border: 1px solid white;
}
</style>
