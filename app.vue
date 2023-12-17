<template>
  <div class="drawer">
    <input id="my-drawer-3" type="checkbox" class="drawer-toggle" />
    <div class="drawer-content flex flex-col">
      <!-- Navbar -->
      <div class="flex-none hidden lg:block">
        <ul class="menu menu-horizontal">
          <!-- Navbar menu content here -->
        </ul>
      </div>
      <!-- Page content here -->
      <div class="h-screen flex p-4 flex-col overflow-auto gap-4">
        <!-- <label
          for="my-drawer-3"
          aria-label="open sidebar"
          class="btn btn-square btn-ghost static"
        >
          <Bars3Icon class="h-8 w-8 text-red-800" />
        </label> -->

        <h1 class="font-mono text-red-800 text-5xl mx-auto">Quotidie</h1>
        <div class="flex flex-col items-center">
          <h2 class="text-grey italic">{{ date }}</h2>
          <h2 class="text-grey italic">{{ messe.informations.ligne1 }}</h2>
        </div>

        <Lectures />
        <Evangile :messe="messe" />
      </div>
    </div>
    <div class="drawer-side">
      <label
        for="my-drawer-3"
        aria-label="close sidebar"
        class="drawer-overlay"
      ></label>
      <ul class="menu p-4 w-80 min-h-full bg-base-200">
        <!-- Sidebar content here -->
      </ul>
    </div>
  </div>
</template>

<script lang="ts" setup>
//@ts-ignore
import { Bars3Icon } from "@heroicons/vue/24/solid";

const date = new Date().toLocaleDateString("fr");

const { data: messe }: any = await useFetch(
  "https://api.aelf.org/v1/messes/2023-12-17/france"
);
</script>

<style>
body {
  background-image: url("/bg.jpg");
  background-repeat: repeat;
}
</style>
