<script setup>
import Badge from "@/components/Badge.vue"
import IconCheck from "@/components/icons/IconCheck.vue";

const COUNTER_MAX = 30

defineProps({
  counter: {
    required: true,
    type: Number
  }
})

</script>

<template>
  <article>
    <div class="img">
      <img src="/auto.png" alt="">
    </div>

    <h1>Mercedes-Benz C-Class</h1>
    <div class="vin">WDB 1400321A333419</div>

    <hr>

    <div class="bottom_info">
      <Badge :type="counter === COUNTER_MAX ? 'success' : 'default'">
        <template v-if="counter === COUNTER_MAX">
          <IconCheck class="check_icon"/>
        </template>
        {{ counter }}/{{COUNTER_MAX}}
      </Badge>
      <span>3 days left</span>
    </div>
  </article>
</template>

<style scoped lang="scss">
@use "@/cfg.scss";

article {
  padding: 1.5rem;
  border-radius: .5rem;
  background-color: #F3F6F8;
}

.img {
  display: flex;
  justify-content: center;
  align-items: center;
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