<template>
  <Mug>
    <Cold v-if="isIced" />
    <Hot v-else />

    <Contents>
      <template #top>
        <Creamer
          v-if="creamer.name !== 'No Creamer'"
          :creamer="creamer"
        />
      </template>

      <template #mid>
        <Syrup
          v-if="syrup.name !== 'No Syrup'"
          :syrup="syrup"
        />
      </template>

      <template #bottom>
        <Base :base="base" />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

import type {
  BaseBeverageType,
  CreamerType,
  SyrupType,
} from "../stores/beverage";

type Props = {
  isIced: boolean;
  base: BaseBeverageType;
  creamer: CreamerType;
  syrup: SyrupType;
};

defineProps<Props>();
</script>