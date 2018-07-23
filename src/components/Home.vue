<template>
  <Page class="page">
    <ActionBar class="action-bar" title="Fifa team generator">
      <NavigationButton text="Go Back" android.systemIcon="ic_menu_back" @tap="$router.push('/home')"/>
    </ActionBar>

    <StackLayout class="fifa-wrapper">
      <SegmentedBar class="segmented-bar" selectedIndex="selectedItem" v-model="selectedItem">
        <SegmentedBarItem title="1v1" />
        <SegmentedBarItem title="2v2" />
      </SegmentedBar>
      <Button class="btn btn-primary" @tap="generateTeam" text="Generate team!"/>

      <TextView v-if="generatedTeam" v-model="generatedTeam.team1[0]" />
      <TextView v-if="generatedTeam" v-model="generatedTeam.team1[1]" />
      <TextView v-if="generatedTeam" text="vs" />
      <TextView v-if="generatedTeam" v-model="generatedTeam.team2[0]" />
      <TextView v-if="generatedTeam" v-model="generatedTeam.team2[1]" />

      <!-- <GridLayout columns="115, 115" rows="115, 115">
        <Label text="0,0" row="0" col="0" backgroundColor="#43b883"/>
        <Label text="0,1" row="0" col="1" backgroundColor="#1c6b48"/>
      </GridLayout> -->

    </StackLayout>

  </Page>
</template>

<script>
  export default {
    data() {
      return {
        selectedItem: 1,
        generatedTeam: null,
      };
    },
    methods: {
      shuffle(a) {
        for (let i = a.length - 1; i > 0; i--) {
          const j = Math.floor(Math.random() * (i + 1));
          [a[i], a[j]] = [a[j], a[i]];
        }
        return a;
      },
      generateTeam() {
        const colors = {
          0: 'blue',
          1: 'red',
          2: 'green',
          3: 'yellow',
        }
        const players = this.shuffle([0, 1, 2, 3])
        this.generatedTeam = {
          team1: {
            0: colors[players[0]],
            1: colors[players[1]],
          },
          team2: {
            0: colors[players[2]],
            1: colors[players[3]],
          }
        }
      },
    },
  };
</script>

<style scoped>
  .fifa-wrapper {
    margin: 20;
  }
</style>
