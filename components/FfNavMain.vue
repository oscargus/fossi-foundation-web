<!--
The main navigation bar

Style guide reference: Web components/Navigation/Navbar

TODO:
- Desktop: the menu items are right-aligned, while (maybe) only the
  "Get involved" button is supposed to be right-aligned, and the remainder of
  the items should be centered.
- Menu items are only marked "active" if the exact page is currently shown, not
  if a child page is chosen. The style guide doesn't mandate a specific
  behavior, but it would probably help users if we marked the top-level item
  as active when a child page is shown.
-->
<template>
  <FfContainer>
    <nav class="py-20 font-black text-ultraviolet">
      <div class="flex flex-wrap items-center justify-between mx-auto">
        <!-- logo -->
        <FfLinkLarge to="/" class="flex-none">
          <span class="sr-only">FOSSi Foundation home page</span>
          <NuxtImg class="w-[180px]" width="180" height="60" alt="The FOSSi Foundation" src="/images/fossi-logo-full.svg" />
        </FfLinkLarge>

        <!-- hamburger icon (phone/tablet only) -->
        <button @click="showMobileNavbar = !showMobileNavbar" type="button" class="inline-flex items-center desktop:hidden" aria-controls="navbar" :aria-expanded="showMobileNavbar">
          <span class="sr-only">Open main menu</span>
          <IconPhList v-if="!showMobileNavbar" class="w-48 h-48"/>
          <IconPhX v-if="showMobileNavbar" class="w-48 h-48"/>
        </button>

        <!-- navigation items -->
        <div class="items-center justify-between w-full desktop:flex desktop:w-auto desktop:order-1" :class="{ 'hidden': !showMobileNavbar }">
          <ul class="flex flex-col desktop:px-16 mt-24 desktop:mt-0 space-y-20 desktop:flex-row desktop:space-y-0 desktop:space-x-16 desktop:items-center">
            <li>
              <FfLinkLarge class="block" to="/">Home</FfLinkLarge>
            </li>
            <li>
              <FfLinkLarge class="block" to="/free-and-open-source-silicon">What is Open Silicon</FfLinkLarge>
            </li>
            <li>
              <FfLinkLarge class="block" to="/about-us">Who we are</FfLinkLarge>
            </li>
            <li>
              <FfLinkLarge class="block" to="/our-work">What we do</FfLinkLarge>
            </li>
            <li>
              <FfLinkLarge class="block" to="/events">Events</FfLinkLarge>
            </li>
            <li>
              <FfLinkLarge class="block" to="/news">News</FfLinkLarge>
            </li>
            <li>
              <FfBtnCta linkTo="/get-involved">Get involved</FfBtnCta>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </FfContainer>
</template>

<script setup lang="ts">
import { ref } from "vue";

import IconPhList from '~icons/ph/list-bold';
import IconPhX from '~icons/ph/x-bold';

// Show the mobile navigation bar? (The desktop navigation bar is always
// visible.) Default to false.
const showMobileNavbar = ref(false);
</script>
