<!-- components/Partners.vue -->
<template>
  <section class="px-4 sm:px-6 md:px-8 lg:px-12 py-10 lg:py-16">
    <div class="mx-auto max-w-7xl text-left md:text-center">
      <p class="text-[#E72700] text-base sm:text-lg font-light">
        TRUSTED PARTNERS
      </p>
      <h1
        class="text-2xl sm:text-3xl md:text-4xl font-bold text-[#292E3E] mt-2"
      >
        Trusted by 1,500+ Universities, Colleges,
        <br class="hidden md:block" />
        and Schools Worldwide
      </h1>
    </div>
    <section class="lg:flex md:flex grid grid-cols-2 lg:gap-5 md:gap-5 gap-2 lg:w-[80%] md:w-[80%] w-full mx-auto">
        <div class="border border-blue-200 rounded-full flex flex-wrap justify-center items-center gap-4 mt-8 p-2 w-auto">
            
                <img
                :src="australia"
                alt="Partner Logo"
                class="lg:h-6 md:h-6 h-5 w-auto object-contain"
                />
           
            <p class="text-base font-medium">Australia</p>
        </div>
        <div class="border border-blue-200 rounded-full flex flex-wrap justify-center items-center w-auto gap-4 mt-8 p-2">
            
                <img
                :src="canada"
                alt="Partner Logo"
                class="lg:h-6 md:h-6 h-5 w-auto object-contain"
                />
            
            <p class="text-base font-medium">Canada</p>
        </div>
        <div class="border border-blue-200 rounded-full flex flex-wrap justify-center items-center w-auto gap-4 mt-8 p-2">
            
                <img
                :src="germany"
                alt="Partner Logo"
                class="lg:h-6 md:h-6 h-5 w-auto object-contain"
                />
          
            <p class="text-base font-medium">Germany</p>
        </div>
        <div class="border border-blue-200 rounded-full flex flex-wrap justify-center items-center gap-4 mt-8 p-2">
            
                <img
                :src="ireland"
                alt="Partner Logo"
                class="lg:h-6 md:h-6 h-5 object-contain"
                />
         
            <p class="text-base font-medium">Ireland</p>
        </div>
        <div class="border border-blue-200 rounded-full flex flex-wrap justify-center items-center gap-4 mt-8 p-2">
            
                <img
                :src="uk"
                alt="Partner Logo"
                class="lg:h-6 md:h-6 h-5 object-contain"
                />
           
            <p class="text-base font-medium">United States</p>
        </div>
        <div class="border border-blue-200 rounded-full flex flex-wrap justify-center items-center gap-4 mt-8 px-2 py-2">
           
                <img
                :src="us"
                alt="Partner Logo"
                class="lg:h-6 md:h-6 h-5 object-contain"
                />
            
            <p class="text-base font-medium">United Kingdom</p>
        </div>
    </section>

    <!-- Responsive grid -->
    <div
      class="mx-auto max-w-7xl mt-8 sm:mt-10 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-3 gap-5 sm:gap-6 lg:gap-8"
    >
      <UniversityCard v-for="p in partners" :key="p.id" :item="p" />
    </div>

    <button
      class="mt-20 bg-[#E72700] text-white text-base px-6 py-2 rounded-lg hover:bg-[#d61f00] transition duration-300 mx-auto block"
    >
      Explore More Irish Institutions
    </button>
  </section>
</template>

<script setup lang="ts">
import UniversityCard from "./UniversityCard.vue";
import australia from "@/assets/australia.png";
import germany from "@/assets/germany.png";
import canada from "@/assets/canada.png";
import ireland from "@/assets/ireland.png";
import uk from "@/assets/uk.png";
import us from "@/assets/us.png";
// === Logos ===
import logo1 from "@/assets/logo/logo1.png";
import logo2 from "@/assets/logo/logo2.png";
import logo3 from "@/assets/logo/logo3.png";
import logo4 from "@/assets/logo/logo4.png";
import logo5 from "@/assets/logo/logo5.png";
import logo6 from "@/assets/logo/logo6.png";
import logo7 from "@/assets/logo/logo7.png";
import logo8 from "@/assets/logo/logo8.png";
import logo9 from "@/assets/logo/logo9.png";
import logo10 from "@/assets/logo/logo10.png";
import logo11 from "@/assets/logo/logo11.png";
import logo12 from "@/assets/logo/logo12.png";
import logo13 from "@/assets/logo/logo13.png";
import logo14 from "@/assets/logo/logo14.png";
import logo15 from "@/assets/logo/logo15.png";
import logo16 from "@/assets/logo/logo16.png";
import logo17 from "@/assets/logo/logo17.png";
import logo18 from "@/assets/logo/logo18.png";

// === Covers ===
import cover1 from "@/assets/girl.jpg";
import cover2 from "@/assets/featured/image2.png";
import cover3 from "@/assets/featured/image3.png";
import cover4 from "@/assets/featured/image4.png";
import cover5 from "@/assets/featured/image5.png";
import cover6 from "@/assets/featured/image6.png";
import cover7 from "@/assets/featured/image7.png";
import cover8 from "@/assets/featured/image8.png";
import cover9 from "@/assets/featured/image9.png";
import cover10 from "@/assets/featured/image10.png";
import cover11 from "@/assets/featured/image11.png";
import cover12 from "@/assets/featured/image12.png";
import cover13 from "@/assets/featured/image13.png";
import cover14 from "@/assets/featured/image14.png";
import cover15 from "@/assets/featured/image15.png";
import cover16 from "@/assets/featured/image16.png";
import cover17 from "@/assets/featured/image17.png";
import cover18 from "@/assets/featured/image18.png";

type Partner = {
  id: number;
  name: string;
  logo: string;
  cover: string;
  title: string;
  text: string;
};

const partners: Partner[] = [
  {
    id: 1,
    name: "Western University",
    logo: logo1,
    cover: cover1,
    title: "London, Ontario, CA",
    text: "Since 1878, Western University has been a choice destination for minds seeking the best education at a research university in Canada. Students at Western University can choose from over 400…",
  },
  {
    id: 2,
    name: "Laurentian University",
    logo: logo2,
    cover: cover2,
    title: "Sudbury, Ontario, CA",
    text: "Laurentian University was once only a regional school serving Sudbury, and while it still serves the area well, it has grown into an international leader in niches such as stressed watershed systems…",
  },
  {
    id: 3,
    name: "Lakehead University",
    logo: logo3,
    cover: cover3,
    title: "Thunder Bay, Ontario, CA",
    text: "Lakehead University is small enough to offer the personalized approach to supports and education that allows students to thrive. And they’re big enough to embody a truly global perspective.",
  },
  {
    id: 4,
    name: "Southern New Hampshire University",
    logo: logo4,
    cover: cover4,
    title: "Manchester, New Hampshire, US",
    text: "Founded in 1932, Southern New Hampshire University, a private, non-profit institution is widely recognized as one of the nation’s most innovative organizations and fastest growing universities…",
  },
  {
    id: 5,
    name: "University of Arizona",
    logo: logo5,
    cover: cover5,
    title: "Tucson, Arizona, US",
    text: "The University of Arizona is a Top 100 university in the world and the first institution in the state of Arizona. As one of the most respected research universities in the United States…",
  },
  {
    id: 6,
    name: "California State University",
    logo: logo6,
    cover: cover6,
    title: "Northridge, California, US",
    text: "Picture a beautiful campus in sunny Los Angeles with acres of green space, palm trees and contemporary architecture. Add academically competitive programs taught by respected scholars and researchers…",
  },
  {
    id: 7,
    name: "Bournemouth University",
    logo: logo7,
    cover: cover7,
    title: "Bournemouth, South West, GB",
    text: "Bournemouth University is an innovative and vibrant public university located in Bournemouth, Dorset, a coastal town famous for its seven-mile stretch of sandy beaches.",
  },
  {
    id: 8,
    name: "University of Greenwich",
    logo: logo8,
    cover: cover8,
    title: "London, Greater London, GB",
    text: "Greenwich is more than a collection of individual students and staff, it is a community of people united by their passion for learning. University of Greenwich courses will give you…",
  },
  {
    id: 9,
    name: "University of Edinburgh",
    logo: logo9,
    cover: cover9,
    title: "Edinburgh, Scotland, GB",
    text: "Founded by the city of Edinburgh in 1583, the University of Edinburgh was the first true civic university in the UK and one of the four ancient universities of Scotland. Join some of the best students from…",
  },
  {
    id: 10,
    name: "Hochschulen Fresenius",
    logo: logo10,
    cover: cover10,
    title: "Berlin, Berlin, DE",
    text: "Hochschule Fresenius began life as the “Chemisches Laboratorium Fresenius” (Fresenius Chemical Laboratory) in 1848 and has evolved into a privately owned German university with a long…",
  },
  {
    id: 11,
    name: "Mediadesign Hochschule",
    logo: logo11,
    cover: cover11,
    title: "Berlin, Berlin, DE",
    text: "For over 35 years, mdh has been guiding students with their expertise and experience into one of the most exciting industries of the present – and future. And they do it exactly where business…",
  },
  {
    id: 12,
    name: "University of Europe for Applied Sciences",
    logo: logo12,
    cover: cover12,
    title: "Iserlohn, Nordrhein-Westfalen, DE",
    text: "The University of Europe for Applied Sciences (UE) is a vibrant and dynamic institution that is dedicated to providing top-quality education to students from all around the world.",
  },
  {
    id: 13,
    name: "Griffith University",
    logo: logo13,
    cover: cover13,
    title: "Southport, Queensland, AU",
    text: "Founded in 1971, Griffith University has become a highly-ranked university with an international outlook. Their teaching and research spans six campuses in South East Queensland and all disciplines…",
  },
  {
    id: 14,
    name: "La Trobe University",
    logo: logo14,
    cover: cover14,
    title: "Bundoora, Victoria, AU",
    text: "Focused on creating a culture of safety, inclusivity, and academic excellence, La Trobe University works to cater to the needs of their community and support students studying with them.",
  },
  {
    id: 15,
    name: "Deakin University",
    logo: logo15,
    cover: cover15,
    title: "Geelong, Victoria, AU",
    text: "Deakin University, founded in 1974, is ranked in the top 1% of universities worldwide (ARWU Rankings, 2020) and is one of the top 50 young universities (QS World University Rankings Top 50…",
  },
  {
    id: 16,
    name: "Dublin Business School",
    logo: logo16,
    cover: cover16,
    title: "Dublin, County of Dublin, IE",
    text: "Founded in 1975, Dublin Business School specialises in the provision of career-focused education. The school has evolved over the years, expanding their offerings to meet the demand of various sectors.",
  },
  {
    id: 17,
    name: "University College Cork",
    logo: logo17,
    cover: cover17,
    title: "Cork, County of Cork, IE",
    text: "On a limestone bluff overlooking the River Lee in Ireland is University College Cork (UCC). Its motto ‘Where Finbarr Taught, Let Munster Learn,’ refers to the 6th century Saint Finbarr, whose monastery …",
  },
  {
    id: 18,
    name: "Trinity College Dublin",
    logo: logo18,
    cover: cover18,
    title: "Dublin, County of Dublin, IE",
    text: "Trinity College Dublin offers undergraduate and postgraduate courses across all major disciplines such as arts and humanities, business, law, engineering, science, maths and health sciences.",
  },
];
</script>
