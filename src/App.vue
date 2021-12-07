/* TODO: 1.Добавление товаров в корзину [], 2.Подключить localeStorage [],
3.Поиск товаров [], 4.Закрытие корзины при нажатии esc [*], 5.Фикс бага карточки
при hover [], */

<template>
  <div class="bg-blue-100 py-10 font-sans">
    <transition name="slide-fade">
      <Drawer
        :cartItems="cartItems"
        :deleteItem="deleteItem"
        :handlerDrawer="handlerDrawer"
        v-if="isDrawerOpen"
      ></Drawer>
    </transition>
    <div class="bg-white rounded-lg max-w-6xl mx-auto shadow-xl">
      <Header :handlerDrawer="handlerDrawer"></Header>
      <div class="p-12">
        <div class="flex justify-between items-center">
          <h1 class=" font-bold text-4xl leading-none">Все кроссовки</h1>
          <div
            v-if="isAppLoaded"
            class="flex p-1 h-12 w-60 border-2 border-gray-200 rounded-2xl items-center"
          >
            <img
              class="w-4 h-4 mr-3 ml-4"
              src="@/assets/img/search.svg"
              alt=""
            />
            <input
              class="text-sm font-normal text-gray-400"
              type="text"
              placeholder="Поиск..."
            />
          </div>
        </div>
        <div class="grid grid-cols-4 mt-10">
          <Card @addToCart="addToCart" :sneakers="sneakers"></Card>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header";
import Drawer from "@/components/Drawer";
import Card from "@/components/Card";

export default {
  name: "App",
  components: { Header, Drawer, Card },
  data() {
    return {
      sneakers: [],
      isAppLoaded: false,
      isDrawerOpen: false,
      cartItems: [],
    };
  },
  methods: {
    getSneakers() {
      setTimeout(async () => {
        const response = await fetch(
          `https://60f5698f18254c00176dfe66.mockapi.io/items`
        );

        const sneakersList = await response.json();
        this.isAppLoaded = true;

        this.sneakers = sneakersList;
      }, 500);
    },
    handlerDrawer() {
      if (this.isDrawerOpen === true) {
        this.isDrawerOpen = false;
        setTimeout(() => {
          document.documentElement.style.overflow = "auto";
        }, 600);
      } else {
        document.documentElement.style.overflow = "hidden";
        this.isDrawerOpen = true;
      }
    },
    escCloseDrawer() {
      document.addEventListener("keydown", (event) => {
        if (event.key === "Escape" && this.isDrawerOpen === true) {
          this.handlerDrawer();
        }
      });
    },

    addToCart(cartItems) {
      this.cartItems.push(cartItems);
    },
    deleteItem(itemToRemove) {
      this.cartItems = this.cartItems.filter((t) => t !== itemToRemove);
    },
   
  
  },

  mounted() {
    this.getSneakers();
    this.escCloseDrawer();
   
  },
};
</script>

<style>
header {
  border-bottom: 1px solid #eaeaea;
}

.rounded4xl {
  border-radius: 40px;
}
.slide-fade-enter-active {
  transition: all 0.5s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(10px);
  opacity: 0;
}
</style>
