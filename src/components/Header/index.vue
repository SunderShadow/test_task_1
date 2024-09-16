<script setup>
import Badge from "@/components/Badge.vue"
import IconPlus from "@/components/icons/IconPlus.vue"
import Avatar from "@/components/Avatar.vue"
import Select from "@/components/Select.vue"

defineProps({
  vechiclesCount: {
    required: true,
    type: Number
  }
})
</script>

<template>
<header>
  <h1>Vechicles</h1>
  <div class="badge"><Badge>{{vechiclesCount}}</Badge></div>
  <button class="add_btn">
    <IconPlus />
  </button>

  <Avatar src="/avatar.png" alt="avatar">John Doe</Avatar>

  <Select src="">
    <img src="/eng.png" alt="eng flag">
    <span>En</span>
  </Select>
</header>
</template>

<style lang="scss" scoped>
@use "@/cfg.scss";

header {
  display: flex;
  align-items: center;

  padding: 2rem 0;
}

h1 {
  font-weight: 700;
  font-size: 2rem;
}

.badge {
  margin-left: 1.1em;
}

.add_btn {
  margin-left: auto;
  width: 42px;
  height: 42px;

  background: none;

  border: 1px solid cfg.$primary-color;
  border-radius: .4em;

  fill: cfg.$primary-color;
}

.avatar, .select {
  margin-left: 2.5rem;
}
</style>