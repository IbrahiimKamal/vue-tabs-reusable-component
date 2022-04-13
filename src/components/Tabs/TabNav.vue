<template>
  <div style="width: 500px; margin: 0 auto">
    <ul>
      <li
        v-for="tab in tabs"
        :key="tab"
        :class="{ 'active-class': tab === selected }"
        @click="selectTab(tab)"
      >
        {{ tab }}
      </li>
    </ul>
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    tabs: {
      type: Array,
      required: true,
    },
    selected: {
      type: String,
      required: true,
    },
  },

  methods: {
    selectTab(tab) {
      this.$emit('select', tab);
    },
  },
};
</script>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

ul {
  list-style: none;
  display: flex;
  justify-content: center;
  align-items: center;
}

li {
  background: rgb(231, 226, 226);
  padding: 1rem 2rem;
  border-radius: 0.25rem;
  cursor: pointer;
}

li:nth-child(2) {
  margin: 0 1rem;
}

.active-class {
  background: #000;
  color: #fff;
  transition: all 1s;
}
</style>
