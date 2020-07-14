<template>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <template #default>
        <Transition css="false" mode="in-out" @enter="() => foo(Component)">
          <component :is="Component" />
        </Transition>
      </template>
      <template #fallback>
        Loading...
      </template>
    </Suspense>
  </RouterView>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "App",
  setup() {
    function foo(cmp: any) {
      console.log(cmp.type.name);
    }

    return { foo };
  },
});
</script>

<style>
:root {
  --ion-toolbar-color: #4b4b4b;
  --ion-color-primary: #306ed9;
}
a {
  text-decoration: none;
  color: black;
}
</style>
