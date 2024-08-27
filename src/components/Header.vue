<script setup>
import { useMenuStore } from "@/store";
const menuStore = useMenuStore();
</script>

<template>
  <div class="wrapper">
    <header class="header">
      <div class="header__logo">
        <img src="../assets/Logo.svg" alt="Логотип" />
      </div>

      <div class="header__menu" @click="menuStore.toggleMenu()">
        <div v-if="!menuStore.isOpen" class="header__burger">
          <div class="header__bar"></div>
          <div class="header__bar"></div>
          <div class="header__bar"></div>
        </div>
        <div v-else class="header__close">
          <img src="../assets/Close.svg" alt="Закрыть" />
        </div>
      </div>

      <div class="header__location" :class="{ header__location_show: menuStore.isOpen }">
        <img src="../assets/SearchCopy.svg" alt="Локация" />
        <p>Москва и область</p>
      </div>

      <div class="header__bell" v-if="!menuStore.isOpen">
        <img src="../assets/Bell.svg" alt="Уведомления" />
      </div>
    </header>
    <nav class="menu" :class="{ menu_show: menuStore.isOpen }">
      <ul>
        <li v-for="menuItem in menuStore.menuItems" :key="menuItem.id">
          <a :href="menuItem.link">{{ menuItem.text }}</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<style scoped lang="scss">
.wrapper {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #000;
}
.header {
  height: 45px;
  display: flex;
  max-width: 1050px;
  justify-content: space-between;
  align-items: center;
  padding: 10px 0;
  width: 90%;
  color: #fff;

  &__logo {
    flex-grow: 1;

    img {
      width: 48px;
      height: 18px;
    }
  }

  &__location {
    display: flex;
    margin-right: 32px;
    color: #7c8792;
    font-size: 14px;
    font-weight: 400;
    line-height: 18px;

    p {
      margin-left: 9px;
      font-size: 14px;
      font-style: normal;
      font-weight: 400;
      line-height: 18px;
    }
  }

  &__burger,
  &__close {
    flex-direction: column;
    cursor: pointer;
    margin-left: 10px;
  }

  &__bar {
    width: 18px;
    height: 2px;
    background-color: #fff;
    margin: 4px 0;
    transition: transform 0.3s ease;
  }

  &__menu {
    display: none;
  }
}

.menu {
  display: block;
  width: 100%;
  background-color: #fff;

  ul {
    list-style: none;
    padding: 0;
    margin: 13px 0 0;
    display: flex;
    gap: 18px;
    justify-content: center;
    flex-wrap: wrap;
  }

  a {
    color: #959597;
    text-decoration: none;
    font-size: 16px;
    font-style: normal;
    font-weight: 700;
    line-height: 22px;

    &:hover {
      text-decoration: underline;
      text-underline-offset: 12px;
      text-decoration-thickness: 2px;
      color: #000;
    }
  }
}

@media (max-width: 375px) {
  .header {
    &__logo {
      order: 1;
    }

    &__location {
      display: none;
      position: absolute;
      bottom: 0px;

      &_show {
        display: flex;
      }
    }

    &__menu {
      display: flex;
      align-items: center;
      cursor: pointer;
      order: 3;
    }

    &__bell {
      display: flex;
      text-align: center;
      order: 2;
    }
  }

  .menu {
    display: none;

    &_show {
      display: flex;
    }

    ul {
      display: flex;
      flex-direction: column;
      margin: 0;
      gap: 0;
    }

    li {
      padding: 16px 0 8px 10px;
      border-bottom: 1px solid #ededed;

      a {
        font-size: 16px;
        font-style: normal;
        font-weight: 700;
        line-height: 22px;
      }
    }
  }
}
</style>
