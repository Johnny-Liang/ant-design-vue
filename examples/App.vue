<template>
  <div style="display: flex; justify-content: center; width: 100%;">
    <a-tree-select
      v-model="value"
      :tree-data="treeData"
      tree-checkable
      :show-checked-strategy="SHOW_PARENT"
      search-placeholder="Please select"
      placement="bottomRight"
      @focus="onfocus"
      @blur="onBlur"
      @dropdownVisibleChange="onDropdownVisibleChange"
    />
  </div>
</template>
<script>
import { TreeSelect } from 'ant-design-vue';
const SHOW_PARENT = TreeSelect.SHOW_PARENT;

const treeData = [
  {
    title: 'Node1',
    value: '0-0',
    key: '0-0',
    children: [
      {
        title: 'Child Node1',
        value: '0-0-0',
        key: '0-0-0',
      },
    ],
  },
  {
    title: 'Node2',
    value: '0-1',
    key: '0-1',
    children: [
      {
        title: 'Child Node3',
        value: '0-1-0',
        key: '0-1-0',
        disabled: true,
      },
      {
        title: 'Child Node4',
        value: '0-1-1',
        key: '0-1-1',
      },
      {
        title: 'Child Node5',
        value: '0-1-2',
        key: '0-1-2',
      },
    ],
  },
];
export default {
  data() {
    return {
      value: ['0-0-0'],
      treeData,
      SHOW_PARENT,
    };
  },
  methods: {
    onfocus(e) {
      console.log('onfocus', e);
    },
    onBlur() {
      console.log('onBlur');
    },
    onDropdownVisibleChange(open) {
      console.log('onDropdownVisibleChange', open);
    },
  },
};
</script>
