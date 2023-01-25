<template>
  <div class="product-card" @mouseover="onHover" @mouseout="onMouseOut">
    <div class="image">
      <img :src="product.image" alt="product image" />
    </div>
    <h3>{{ product.title }}</h3>
    <p>{{ product.price }}$</p>
    <transition-group name="fade">
      <div v-if="hovering" class="extra-info" key="description">
        <p>{{ product.description }}</p>
      </div>
    </transition-group>
  </div>
</template>
<script>
export default {
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      hovering: false,
    }
  },
  methods: {
    onHover() {
      this.hovering = true
      this.$emit('mouseover', this.product)
      this.$el.classList.add('scaled')
    },
    onMouseOut() {
      this.hovering = false
      this.$el.classList.remove('scaled')
    },
  },
}
</script>
<style>
.product-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  border: 3px solid teal;
  border-radius: 15px;
}

.product-card.scaled {
  transform: scale(1.1);
  transition: 1s;
}

img {
  height: 300px;
}

.extra-info {
  padding: 0 50px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
