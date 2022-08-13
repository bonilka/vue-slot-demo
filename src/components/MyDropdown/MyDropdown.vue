<template>
  <div class="dropdown">
    <input
      :value="modelValue"
      type="text"
      class="dropdown__input"
      @focus="focused = true"
      @blur="focused=false"
    >
    <MyDropdownList
      :options="options"
      @chose="onChose"
    >
      <template #option="{option}">
        <slot
          name="option"
          v-bind="{option}"
          :active="modelValue === option.title"
        />
      </template>
    </MyDropdownList>
  </div>
</template>

<script>
import MyDropdownList from './MyDropdownList.vue'

export default {
    components: {
        MyDropdownList
    },
    props: {
        modelValue: {
            type: String,
            default: "",
        },
        options: {
            type: Array,
            default: () => [],
        },
    },
    emits: ['update:modelValue'],
    data() {
        return {
            focused: false,
        };
    },
    methods: {
        onChose({title}) {
            this.$emit('update:modelValue', title);
        }
    }
};
</script>

<style scoped>
.dropdown {
    --dropdown-border-radius: 8px;

    display: inline-block;
    width: 350px;
}

.dropdown__input {
    display: block;
    width: 100%;
    height: 100%;
    padding: 14px 10px;
    line-height: 1.75;
    border: none;
    font-size: 1.5rem;
    border: 1px solid var(--color-border);
    border-radius: var(--dropdown-border-radius);
    color: inherit;
}

.dropdown__input:hover {
    border-color: var(--color-border-hover);
}

.dropdown__input:focus {
    border-color: var(--color-theme);
    outline: 2px solid var(--color-theme);
}
</style>