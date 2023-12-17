<template>
  <div
    class="border-2 border-red-800 rounded-md w-full p-4 shadow-2xl flex flex-col gap-4"
  >
    <div class="text-black text-xl underline">Evangile du jour</div>
    <div class="text-black" v-html="evangile"></div>
  </div>
</template>

<script lang="ts" setup>
const props = defineProps<{
  messe: any;
}>();

const evangile = computed(() => {
  if (!props.messe) return "";
  if (props.messe.messes.length == 0) return "";

  for (const messe of props.messe.messes) {
    if (messe.nom == "Messe du jour") {
      return messe.lectures.filter((el) => el.type == "evangile")[0].contenu;
    }
  }
});
</script>
