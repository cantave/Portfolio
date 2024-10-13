<template>
  <div class="item">
    <i>
      <slot name="icon"></slot>
    </i>
    <div class="details">
      <h3>
        <slot name="heading"></slot>
      </h3>
      <slot></slot>
    </div>
  </div>
</template>

<style scoped>
.item {
  margin: 1.5rem 0;
  display: flex;
  align-items: center;

}

.details {
  flex: 1;
  margin-left: 1rem;
}

i {
  font-size: 2rem;
  color: var(--color-text);
}

h3 {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  font-family: 'Source Sans Pro', sans-serif;
}

</style>
