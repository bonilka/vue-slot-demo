<template>
  <div>
    <slot>
      {{ title }}
    </slot>
  </div>
</template>

<script>
export default {
    props: {
        title: {
            type: String,
            default: ''
        }
    },
    inject: ['addUpdate'],
    updated() {
        this.addUpdate();
        console.log('updated-item');
    },
}
</script>