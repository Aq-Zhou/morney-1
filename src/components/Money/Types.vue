<template>
  <div class="types">
    <li :class="value === '-' && 'selected'"
        @click="selectType('-')">支出
    </li>
    <li :class="value === '+' && 'selected'"
        @click="selectType('+')">收入
    </li>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import {Component, Prop} from 'vue-property-decorator';

@Component
export default class Types extends Vue {
  // type = '-'  //'-'表支出，'+' 表收入
  @Prop() readonly value!: string;

  selectType(type:string) {  //type只能是'-' 和 '+' 中的一个
    if(type !== '-' && type !== '+' ){
      throw new Error ('type is unknown');
    }
    this.$emit('update:value' , type);
  }
}

// export default class Types from Vue {
  // type = '-'
 // @Prop(Number) Types : number | undefined;



// export default {
//   name: 'Types',
//   data() {
//     return {
//       type:'-' //'-'表支出，'+' 表收入
//     }
//   },
//   methods: {
//     selectType(type) { //type只能是'-' 和 '+' 中的一个
//       if(type !== '-' && type !== '+'){
//         throw new Error('type is unknown')
//       }
//       this.type = type
//     }
//   }
// };
</script>

<style lang="scss" scoped>
.types {
  background: #c4c4c4;
  display: flex;
  text-align: center;
  font-size: 24px;
  > li {
    width: 50%;
    height: 64px;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    &.selected::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 4px;
      background: #333333;
    }
  }
}
</style>