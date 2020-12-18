<template>
  <v-tooltip bottom>
    <template v-slot:activator="{ on }">
      <span v-on="on">
        <v-img 
            :src="icon"
            :max-height="10"
            :max-width="10"
        ></v-img>
      </span>
    </template>
    Flo Enabled
  </v-tooltip>
</template>

<script lang="ts">
import Vue from "vue";
import { Component } from "vue-property-decorator";

@Component({})
export default class FloIndicator extends Vue {

    get icon() : unknown {
        return require("@/assets/icons/FLO.png")
    }
}
</script>

<style></style>
