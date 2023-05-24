<template>
  <div
    class="h-[550px] w-[700px] bg-[rgb(0,0,0,.4)] rounded-lg border border-black border-2 text-center"
  >
    <h1 class="text-white mt-5 font-semibold text-3xl">Wheather App</h1>
    <input
      type="text"
      placeholder="...search"
      class="w-[500px] h-10 search border rounded-lg pl-5 mt-7 text-white"
      @input="
        (e) => {
          this.$emit('update:modelValue', e.target.value);
        }
      "
    />
    <div class="w-[500px] mx-auto mt-5 bg-black text-white">
      <div v-for="info in infos">
        <div
          @click="this.$emit('getInfo',info.url)"
          class="w-full h-10 text-start pl-5 flex items-center cursor-pointer"
        >
          <h1>{{ info.url }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    props: {
      modelValue: String,
    },
    infos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    getInfo() {},
  },
};
</script>

<style></style>
