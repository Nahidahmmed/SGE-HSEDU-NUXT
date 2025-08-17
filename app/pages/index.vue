<script setup lang="ts">
import Applications from "~/components/Applications.vue";
import Banner from "~/components/Banner.vue";
import ChannelPartners from "~/components/ChannelPartners.vue";
import GetStarted from "~/components/GetStarted.vue";
import Partners from "~/components/Partners.vue";
import Programs from "~/components/Programs.vue";
import Review from "~/components/Review.vue";
import SearcheForm from "~/components/SearcheForm.vue";
import StudyAbroad from "~/components/StudyAbroad.vue";
import StudyProgram from "~/components/StudyProgram.vue";

definePageMeta({
  layout: "default",
});
</script>

<template>
  <main class="bg-white">
    <section class="max-w-screen-xl mx-auto px-3">
      <Banner />
      <section class="absolute z-50 w-[94%] px-0 md:px-8 max-w-screen-xl
                top-[550px] sm:-top-14 md:-top-16 lg:top-[520px] xl:top-[550px]">
        <SearcheForm />
      </section>
      <StudyAbroad />
      <StudyProgram />
      <Applications />
      <Review />
      <Partners />
      <ChannelPartners />
      <Programs />
      <FaqSection />
      <GetStarted />
    </section>
  </main>
</template>


