<template>
  <Window title="计算器" width="100" height="100" margined v-on:close="exit" ref="mainWindow">
    <Box horizontal padded>
      <Group stretchy margined>
        <Box padded>
          <Box>
            <TextInput v-model="text" readonly="true"/>
          </Box>
          <Box padded margined horizontal="true">
            <Button stretchy v-on:click="click(1)">1</Button>
            <Button stretchy v-on:click="click(2)">2</Button>
            <Button stretchy v-on:click="click(3)">3</Button>
            <Button stretchy v-on:click="click('+',true)">+</Button>
          </Box>
          <Box padded margined horizontal="true">
            <Button stretchy v-on:click="click(4)">4</Button>
            <Button stretchy v-on:click="click(5)">5</Button>
            <Button stretchy v-on:click="click(6)">6</Button>
            <Button stretchy v-on:click="click('-',true)">-</Button>
          </Box>
          <Box padded margined horizontal="true">
            <Button stretchy v-on:click="click(7)">7</Button>
            <Button stretchy v-on:click="click(8)">8</Button>
            <Button stretchy v-on:click="click(9)">9</Button>
            <Button stretchy v-on:click="click('*',true)">*</Button>
          </Box>
          <Box padded margined horizontal="true">
            <Button stretchy v-on:click="click(0)">0</Button>
            <Button stretchy v-on:click="cal('=')">=</Button>
            <Button stretchy v-on:click="clear()">C</Button>
            <Button stretchy v-on:click="click('/',true)">/</Button>
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
        hasSymbol:false,
      };
    },
    methods: {
      exit() {
        libui.stopLoop();
      },
      click(num,flag) {
        if(flag&&this.hasSymbol){
          this.cal('=');
          this.hasSymbol=false;
          return
        }
        if(flag){
          this.hasSymbol=true;
        }

        this.text += num;
      },
      cal(symbol) {
        this.text = eval(this.text)
      },
      clear() {
        this.text = ''
      },
    }
  }
</script>
