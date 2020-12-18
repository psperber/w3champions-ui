<template>
  <div>
    <div
      v-for="(player, index) in team.players"
      v-bind:key="index"
      v-bind:class="{ mt2: index > 0 }"
    >
      <player-match-info
        :unfinishedMatch="unfinishedMatch"
        :player="team.players[index]"
        :left="left"
        :big-race-icon="bigRaceIcon"
        :not-clickable="notClickable"
        :is-anonymous="isAnonymous"
        :usingFlo="usingFlo(player)"
      />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { Component, Prop } from "vue-property-decorator";
import { Team , ServerInfo } from "@/store/typings";
import PlayerMatchInfo from "@/components/matches/PlayerMatchInfo.vue";

@Component({
  components: { PlayerMatchInfo },
})
export default class TeamMatchInfo extends Vue {
  @Prop() public team!: Team;
  @Prop() public left!: boolean;
  @Prop() public bigRaceIcon!: boolean;
  @Prop() public notClickable!: boolean;
  @Prop() public unfinishedMatch!: boolean;
  @Prop() public isAnonymous!: boolean;
  @Prop() public serverInfo!: ServerInfo;

  usingFlo(player): boolean {

    // this function will tell the playerMatchInfo whether to show the "Flo Enabled" icon so that you can see which player in a Bnet game does not have Flo on.

    if (this.serverInfo.provider != 'FLO') {
      return true;
    }

    // WIP

    if (this.serverInfo) {
      console.log(this.serverInfo)
    }

    // let playerPingData = this.serverInfo.playerServerInfos;

    // console.log(this.serverInfo)

    // for (let element in playerPingData) {
    //   if (playerPingData[element].battleTag == player && playerPingData[element].averagePing.typeof == "number") {
    //     return true;
    //   }
    // }

    return false;
  }

} 
</script>
