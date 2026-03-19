<template>
  <div>
    <Beverage
      :isIced="currentTemp === 'Cold'"
      :base="currentBase"
      :creamer="currentCreamer"
      :syrup="currentSyrup"
    />

    <ul>
      <li>
        <strong>Temperature:</strong>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>

      <li>
        <label><strong>Base Beverage:</strong></label>
        <select v-model="currentBase">
          <option v-for="base in bases" :key="base.id" :value="base">
            {{ base.name }}
          </option>
        </select>
      </li>

      <li>
        <label><strong>Creamer:</strong></label>
        <select v-model="currentCreamer">
          <option v-for="creamer in creamers" :key="creamer.id" :value="creamer">
            {{ creamer.name }}
          </option>
        </select>
      </li>

      <li>
        <label><strong>Syrup:</strong></label>
        <select v-model="currentSyrup">
          <option v-for="syrup in syrups" :key="syrup.id" :value="syrup">
            {{ syrup.name }}
          </option>
        </select>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import {
  temps,
  bases,
  creamers,
  syrups,
  currentTemp,
  currentBase,
  currentCreamer,
  currentSyrup,
} from "./stores/beverage";
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

li {
  margin-bottom: 12px;
  color: white;
}

label {
  margin-right: 10px;
}

select {
  margin-left: 8px;
  padding: 4px 8px;
  border-radius: 6px;
  border: none;
}
</style>