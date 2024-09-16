<script setup>
import Badge from "@/components/Badge.vue"
import IconCheck from "@/components/icons/IconCheck.vue";

const COUNTER_MAX = 30

defineProps({
  uploads: {
    required: true,
    type: Number
  },
  vin: {
    required: true,
    type: String
  },
  name: {
    required: true,
    type: String
  },
  img: {
    required: true,
    type: String
  }
})

</script>

<template>
  <article>
    <div class="img">
      <img :src="img" alt="">
    </div>

    <h1>{{ name }}</h1>
    <div class="vin">{{ vin }}</div>

    <hr>

    <div class="bottom_info">
      <Badge :type="uploads === COUNTER_MAX ? 'success' : 'default'">
        <template v-if="uploads === COUNTER_MAX">
          <IconCheck class="check_icon"/>
        </template>
        {{ uploads }}/{{ COUNTER_MAX }}
      </Badge>
      <span>3 days left</span>
    </div>
  </article>
</template>

<style scoped lang="scss">
@use "@/cfg.scss";

article {
  display: flex;
  flex-direction: column;

  padding: 1.5rem;
  border-radius: .5rem;
  background-color: #F3F6F8;
}

.img {
  width: 100%;

  display: flex;
  flex-grow: 1;
  justify-content: center;
  align-items: center;

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}

h1 {
  margin-top: 1.5rem;
  font-size: 1.5rem;
}

.vin {
  opacity: .6;
  margin-top: .75rem;
}

hr {
  margin-top: 1rem;
  margin-bottom: 1rem;
}

.bottom_info {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.badge {
  background-color: #EDEDED;
}
.check_icon {
  fill: none;
  transform: translate(-2px, 3px);
}
</style>