<template>
  <div
    @click.self="handlerDrawer"
    class="absolute z-10 inset-0 bg-black bg-opacity-10 w-full h-full"
  >
    <div
      class="w-96 bg-white shadow-2xl absolute right-0 h-full p-8 flex flex-col"
    >
      <div class="flex justify-between mb-8">
        <h2 class="m-0 text-xl font-bold">Корзина</h2>
        <button @click.stop="handlerDrawer">
          <svg
            class="opacity-50 transition-opacity duration-300 hover:opacity-100"
            width="32"
            height="32"
            viewBox="0 0 32 32"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M20.0799 18.6155L17.6311 16.1667L20.0798 13.718C21.0241 12.7738 19.5596 11.3093 18.6154 12.2536L16.1667 14.7023L13.7179 12.2535C12.7738 11.3095 11.3095 12.7738 12.2535 13.7179L14.7023 16.1667L12.2536 18.6154C11.3093 19.5596 12.7738 21.0241 13.718 20.0798L16.1667 17.6311L18.6155 20.0799C19.5597 21.0241 21.0241 19.5597 20.0799 18.6155Z"
              fill="#B5B5B5"
            />
          </svg>
        </button>
      </div>
      <div class="flex-1">
        <div
          v-for="cartSneaker in cartItems"
          :key="cartSneaker.name"
          class="flex items-center border-gray-300 border-2 rounded-3xl p-5 mb-5"
        >
          <img
            class="w-16"
            :src="require(`@/assets/img/sneakers/${cartSneaker.imageUrl}.jpg`)"
            alt="sneakers"
          />
          <div class="ml-5 mr-3">
            <p class="font-normal text-base leading-none mb-2">
              {{ cartSneaker.name }}
            </p>
            <strong class="font-bold">{{ cartSneaker.price }}</strong>
          </div>
          <button @click="deleteItem(cartSneaker)">
            <svg
              class="opacity-50 transition-opacity duration-300 hover:opacity-100"
              width="32"
              height="32"
              viewBox="0 0 32 32"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <rect
                x="0.5"
                y="0.5"
                width="31"
                height="31"
                rx="7.5"
                fill="white"
                stroke="#DBDBDB"
              />
              <path
                d="M20.0799 18.6155L17.6311 16.1667L20.0798 13.718C21.0241 12.7738 19.5596 11.3093 18.6154 12.2536L16.1667 14.7023L13.7179 12.2535C12.7738 11.3095 11.3095 12.7738 12.2535 13.7179L14.7023 16.1667L12.2536 18.6154C11.3093 19.5596 12.7738 21.0241 13.718 20.0798L16.1667 17.6311L18.6155 20.0799C19.5597 21.0241 21.0241 19.5597 20.0799 18.6155Z"
                fill="#B5B5B5"
              />
            </svg>
          </button>
        </div>
      </div>
      <ul>
        <li class="flex items-end mb-5">
          <span>Итого:</span>
          <div
            class="h-1 mx-3 border-b-2 border-dashed border-gray-300 flex-1 relative -top-1"
          ></div>
          <strong>21 498 руб</strong>
        </li>
        <li class="flex items-end mb-5">
          <span>Налог 5%:</span>
          <div
            class="h-1 mx-3 border-b-2 border-dashed border-gray-300 flex-1 relative -top-1"
          ></div>
          <strong>1074 руб</strong>
        </li>
      </ul>
      <button
        class="green_btn rounded-lg py-3 font-bold text-white transition transform-gpu duration-200 hover:shadow-lg hover:translate-x-0.5"
      >
        <div
          class="transform-gpu transition duration-300 hover:translate-x-0.5"
        >
          Оформить заказ<svg
            class="inline ml-5 transform-gpu hover:translate-x-0.5"
            width="16"
            height="14"
            viewBox="0 0 16 14"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M1 7H14.7143"
              stroke="white"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M8.71436 1L14.7144 7L8.71436 13"
              stroke="white"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    handlerDrawer: {
      type: Function,
    },
    cartItems: {
      type: Array,
    },
    deleteItem: {
      type: Function,
    },
  },
  data() {
    return {
    }
  },
  methods:{
  
  }
};
</script>

<style scoped>
.green_btn {
  background-color: #9dd458;
}
</style>
