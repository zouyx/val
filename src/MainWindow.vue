<template>
  <Window title="Test" width="400" height="100" margined v-on:close="exit">
    <Box>
      <Text>Welcome to your Test application!</Text>
      <Button v-on:click="ok">OK</Button>
      <Button v-on:click="cancel">Cancel</Button>
    </Box>
  </Window>
</template>

<script>
import libui from 'libui-node'

export default {
  methods: {
    exit() {
      libui.stopLoop();
    },
    ok(){
      console.log("ok!")
    },
    cancel(){
      console.log("cancel!")
    }

  }
}
</script>
