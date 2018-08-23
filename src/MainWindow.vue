<template>
  <Window title="计算器" width="100" height="100" margined v-on:close="exit" ref="mainWindow">
    <Box horizontal padded>
      <Group stretchy>
        <Box>
          <TextInput v-model="text" readonly="true"/>
          <Box padded margined horizontal="true">
            <Button v-on:click="click(0)">0</Button>
            <Button v-on:click="click(1)">1</Button>
            <Button v-on:click="click(2)">2</Button>
            <Button v-on:click="click(3)">3</Button>
            <Button v-on:click="click(4)">4</Button>
          </Box>
          <Box padded margined horizontal="true">
            <Button v-on:click="click(5)">5</Button>
            <Button v-on:click="click(6)">6</Button>
            <Button v-on:click="click(7)">7</Button>
            <Button v-on:click="click(8)">8</Button>
            <Button v-on:click="click(9)">9</Button>
          </Box>
          <Box padded margined horizontal="true">
            <Button v-on:click="click('+')">+</Button>
            <Button v-on:click="click('-')">-</Button>
            <Button v-on:click="click('*')">*</Button>
            <Button v-on:click="click('/')">/</Button>
            <Button v-on:click="cal('=')">=</Button>
          </Box>
          <Button @click="selectFile">Browse...</Button>
        </Box>
      </Group>
    </Box>
  </Window>
</template>

<script>
  import libui from 'libui-node'

  export default {
    data() {
      return {
        text: '',

      };
    },
    methods: {
      exit() {
        libui.stopLoop();
      },
      click(num) {
        this.text += num;
      },
      cal(symbol) {
        this.text = eval(this.text)
      },
      selectFile() {
        const window = this.$refs.mainWindow.window;
        const filename = libui.UiDialogs.openFile(window);
        if (filename) {
          console.log(filename)
        }
      }
    }
  }
</script>
