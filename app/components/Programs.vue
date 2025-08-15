
<template>
  <section class="w-full lg:p-0 md:p-0 p-4">
    <div
      class="relative overflow-hidden rounded-2xl bg-gradient-to-r from-[#2E6CF6] to-[#0542a3] lg:h-[300px]"
    >
      <div
        class="relative mx-auto max-w-7xl px-4 sm:px-6 py-6 sm:py-8 lg:px-6 lg:py-6"
      >
        <div class="flex flex-col items-center gap-6 sm:gap-8 lg:flex-row">
          <!-- IMAGE — hidden on mobile -->
          <div
            class="hidden lg:flex relative w-full lg:w-[44%] justify-center lg:justify-start"
          >
            <!-- Concentric circle behind character -->
            <div
              class="absolute left-1/2 top-1/2 -translate-x-1/2 -translate-y-1/2 h-[500px] w-[500px] opacity-30"
              style="
                background: radial-gradient(
                  circle,
                  rgba(255, 255, 255, 0.25) 0%,
                  rgba(255, 255, 255, 0.15) 40%,
                  rgba(255, 255, 255, 0.06) 70%,
                  rgba(255, 255, 255, 0) 72%
                );
                border-radius: 9999px;
              "
            />
            <div
              class="w-72 h-72 border-[40px] ml-5 mt-3 border-[#3671f0] rounded-full"
            >
              <div
                class="w-64 h-64 border-[40px] border-[#3671f0] rounded-full relative right-7"
              />
            </div>
            <img
              src="/assets/boy.png"
              alt="Student"
              width="520"
              height="520"
              class="h-[280px] w-auto object-contain absolute z-10"
            />
          </div>

          <!-- TEXT AREA -->
          <div class="w-full lg:w-[80%] text-white text-left relative z-10 p-5">
            <h2
              class="text-2xl md:text-3xl lg:text-4xl font-extrabold leading-snug text-white"
            >
              Choose from 140,000+ Study Programs
            </h2>

            <p
              class="mt-3 text-sm md:text-base lg:text-lg/7 text-white/90 max-w-2xl mx-auto lg:mx-0"
            >
              Pick your programs. Apply all at once. Built-in quality checks
              give you a ~95% chance of application success.
            </p>

            <div class="mt-6">
              <a
                href="#"
                class="inline-block rounded-md bg-white px-5 py-2.5 text-[#184FCB] font-semibold shadow-sm hover:bg-gray-100 transition"
              >
                Start Your Journey
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// No logic needed — static content
</script>
