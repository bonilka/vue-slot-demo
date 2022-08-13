<template>
  <ul class="dropdown-list">
    <li
      v-for="item in options"
      :key="item.id"
      class="dropdown-list__option"
      @click="onClick(item)"
    >
      <MyOption :title="item.title">
        <!-- the problem  -->
        <slot
          v-if="$slots.option"
          name="option"
          :option="item"
        />
      </MyOption>
    </li>
  </ul>
</template>

<script>
import MyOption from "./MyOption.vue";
export default {
    components: {
        MyOption,
    },
    props: {
        options: {
            type: Array,
            default: () => [],
        },
    },
    inject: ['resetChildrenUpdated'],
    emits: ["chose"],
    beforeUpdate() {
      this.resetChildrenUpdated();
    },
    methods: {
        onClick(item) {
            this.$emit("chose", item);
        },
    },
};
</script>

<style scoped>
.dropdown-list {
    list-style: none;
    text-align: left;
    margin: 0 auto;
    padding: 0;
}

.dropdown-list__option {
    cursor: pointer;
    padding: 16px 8px;
    border-bottom: 1px solid var(--color-border);
    transition: background-color 0.15s;
}

.dropdown-list__option:hover {
    background-color: #eee;
}
</style>