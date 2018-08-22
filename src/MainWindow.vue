<template>
  <Window title="Test Demo" width="100px" v-on:close="exit">
    <Box horizontal padded>
      <Group stretchy title="计算器">
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
    }
  }
</script>
