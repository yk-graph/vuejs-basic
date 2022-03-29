<template>
  <h1>This is Example Tab Page</h1>
  <section class="tab">
    <ul class="tab__label">
      <li v-for="item in items" :key="item.id">
        <a
          href="#"
          @click.prevent="activate(item.id)"
          :class="{ active: active === item.id }"
          >{{ item.title }}</a
        >
      </li>
    </ul>

    <div class="tab__content" v-show="active === 1">
      サイトの情報。サイトの情報。
    </div>
    <div class="tab__content" v-show="active === 2">商品情報。商品情報。</div>
    <div class="tab__content" v-show="active === 3">
      お問い合わせ。お問い合わせ。
    </div>
  </section>
</template>

<script>
import { ref, reactive } from 'vue'
export default {
  setup() {
    const active = ref(1)
    const items = reactive([
      { id: 1, title: 'サイトの情報' },
      { id: 2, title: '商品情報' },
      { id: 3, title: 'お問い合わせ' },
    ])

    const activate = (id) => (active.value = id)

    return {
      active,
      items,
      activate,
    }
  },
}
</script>

<style lang="scss" scoped>
.tab {
  font-size: 14px;
  margin: 20px auto;
  width: 600px;
  &__label {
    list-style: none;
    padding: 0;
    margin: 0;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
  &__label li a {
    display: inline-block;
    width: 130px;
    text-align: center;
    padding: 8px 0;
    color: #333;
    text-decoration: none;
    border-radius: 10px 10px 0 0;
  }
  &__label li a.active {
    background: #e6f0ff;
  }
  &__label li a:not(.active):hover {
    opacity: 0.5;
    -webkit-transition: 0.4s;
    transition: 0.4s;
  }
  &__content {
    background: #e6f0ff;
    font-size: 16px;
    min-height: 150px;
    padding: 15px;
    display: block;
  }
}
</style>
