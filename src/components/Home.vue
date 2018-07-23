<template>
  <Page class="page">
    <ActionBar class="action-bar" title="Fifa">
      <NavigationButton text="Go Back" android.systemIcon="ic_menu_back" @tap="$router.push('/home')"/>
    </ActionBar>

    <StackLayout class="fifa-wrapper">
      <Label class="body" textWrap=true text="This is a Fifa component"/>

      <Button class="btn btn-primary" @tap="log" text="Tap me!"/>
    </StackLayout>

  </Page>
</template>

<script>
  export default {
    data() {
      return {
        surprise: false,
      };
    },
    methods: {
      log() {
        console.log('Pressed the button!')
      }
    },
  };
</script>

<style scoped>
  .hello-world {
    margin: 20;
  }

  Label {
    color: green;
    font-size: 25px;
    text-align: center;
  }
</style>
