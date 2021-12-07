<template>
  <div
    v-for="sneakers in sneakers"
    :key="sneakers.name"
    class="w-52 mx-auto border-gray-200 border-2 rounded4xl p-5 shadow-sm mb-10 transform-gpu hover:-translate-y-2 hover:shadow-xl transition duration-500"
  >
    <img
      :src="require(`@/assets/img/sneakers/${sneakers.imageUrl}.jpg`)"
      alt="sneakers"
      class="mb-4"
    />
    <p class="mb-4 text-sm font-normal">
      {{ sneakers.name }}
    </p>
    <div class="flex justify-between">
      <div class="flex flex-col">
        <span class="text-xs font-medium text-gray-4">Цена:</span>
        <strong class="font-bold text-sm">{{ sneakers.price }}руб.</strong>
      </div>
      <button @click="addToCart(sneakers)">
        <img
          :src="require('@/assets/img/plus.svg')"
          @click="plus(sneakers)"
          alt=""
          class="opacity-50 transition-opacity duration-300 hover:opacity-100"
        />
      </button>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    sneakers: {
      type: Array,
      required: true,
    },
  },
  emits: ["addToCart"],

  data() {
    return {};
  },
  methods: {
    addToCart(obj) {
     
      this.$emit("addToCart", obj);
    },
    plus(obj){
      let q = obj

      console.log(q);
    }
  },
};
</script>
<style scoped>
.rounded4xl {
  border-radius: 40px;
}
</style>
