<template>
  <div
    class="border-2 border-red-800 rounded-md w-full p-4 shadow-2xl flex flex-col gap-4"
  >
    <div class="text-black text-xl underline">
      Lire la bible en un an <span class="font-bold">{{ info }}</span>
    </div>

    <div class="flex justify-around w-full">
      <a
        :href="link(l)"
        target="_blank"
        v-for="l in lectures"
        class="gap-4 px-4 py-2 flex items-center cursor-pointer hover:bg-red-950 bg-red-800 border-0 text-white rounded-md"
      >
        <span>{{ l }} </span>
        <ArrowRightIcon class="h-6 w-6 text-white" />
      </a>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ArrowRightIcon } from "@heroicons/vue/24/solid";

const date = new Date().toLocaleDateString("fr");
const d = date.split("/")[0];
const m = date.split("/")[1];
const info: any = ref();
const data: any = ref((await queryContent("/data").findOne()).body);

const lectures = computed(() => {
  const infos = data.value[Number(d) + 1][months[Number(m) - 1]];
  return infos.split("&").map((el: string) => el.trim());
});

function link(lecture: string) {
  const url = lecture.replace(" ", "/").split("-")[0];
  return `https://www.aelf.org/bible/${url}`;
}

const months = [
  "janvier",
  "fevrier",
  "mars",
  "avril",
  "mai",
  "juin",
  "juillet",
  "aout",
  "septembre",
  "octobre",
  "novembre",
  "decembre",
];
</script>
