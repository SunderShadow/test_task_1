<script setup>

import SidebarMenuItem from "./MenuItem.vue"

import IconProfile     from "@/components/icons/IconProfile.vue"
import IconVechicles   from "@/components/icons/IconVechicles.vue"
import IconSettings    from "@/components/icons/IconSettings.vue"
</script>

<template>
  <aside>
    <h1>Demo Test</h1>

    <div class="menu">
      <SidebarMenuItem active>
        <template v-slot:icon>
          <IconProfile/>
        </template>

        Profile
      </SidebarMenuItem>

      <SidebarMenuItem>
        <template v-slot:icon>
          <IconVechicles/>
        </template>

        Vechicles
      </SidebarMenuItem>

      <SidebarMenuItem>
        <template v-slot:icon>
          <IconSettings/>
        </template>

        Settings
      </SidebarMenuItem>
    </div>
    <div class="decor"></div>
  </aside>
</template>

<style lang="scss" scoped>
@use "@/cfg";

aside {
  position: relative;

  height: 100vh;

  color: #fff;
  background-color: cfg.$sidebar-color;
}

h1 {
  font-size: 1.5rem;
  font-weight: 700;

  margin: 1.5rem 4rem;
}

.menu {
  display: flex;
  flex-direction: column;
  gap: .75em;

  margin-top: 6rem;
}

.decor {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 15rem;
  background-image: url("/sidebar_decor.png");
}
</style>