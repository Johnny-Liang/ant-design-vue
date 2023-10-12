<template>
  <a-table :columns="columns" :data-source="data">
    <template slot="name" slot-scope="text">{{ text }}</template>
    <span slot="customTitle"><a-icon type="smile-o" /> Name</span>
    <span slot="age1">fds</span>
    <span slot="tags" slot-scope="tags">
      <a-tag
        v-for="tag in tags"
        :key="tag"
        :color="tag === 'loser' ? 'volcano' : tag.length > 5 ? 'geekblue' : 'green'"
      >
        {{ tag.toUpperCase() }}
      </a-tag>
    </span>
    <span slot="action" slot-scope="text, record">
      <a @click="log">Invite 一 {{ record.name }}</a>
      <a-divider type="vertical" />
      <a>Delete</a>
      <a-divider type="vertical" />
      <a class="ant-dropdown-link"> More actions <a-icon type="down" /> </a>
    </span>
    <p slot="expandedRowRender" style="margin: 0">
      ./node_modules/babel-loader/lib??ref--1!./node_modules/vue-loader/lib??vue-loader-options!./examples/App.vue?vue&type=script&lang=js&
    </p>
  </a-table>
</template>
<script>
const columns = [
  {
    dataIndex: 'name',
    key: 'name',
    slots: { title: 'customTitle' },
    scopedSlots: { customRender: 'name' },
  },
  {
    title: 'Age',
    dataIndex: 'age0',
    key: 'age',
    children: [
      {
        dataIndex: 'age1',
        title: 'age1',
        scopedSlots: { customRender: 'age1' },
        customRender: text => {
          return '321';
        },
      },
      {
        dataIndex: 'age',
        title: 'age2',
      },
    ],
  },
  {
    title: 'Address',
    dataIndex: 'address',
    key: 'address',
    customRender: text => {
      return {
        attrs: {
          copyText: text,
        },
        children: ['fds'],
      };
    },
  },
  {
    title: 'Tags',
    key: 'tags',
    dataIndex: 'tags',
    scopedSlots: { customRender: 'tags' },
  },
  {
    title: 'Action',
    key: 'action',
    scopedSlots: { customRender: 'action' },
  },
];

const data = [
  {
    key: '1',
    name: 'John Brown',
    age: 32,
    address: 'New York No. 1 Lake Park',
    tags: ['nice', 'developer'],
  },
  {
    key: '2',
    name: 'Jim Green',
    age: 42,
    address: 'London No. 1 Lake Park',
    tags: ['loser'],
  },
  {
    key: '3',
    name: 'Joe Black',
    age: 32,
    address: 'Sidney No. 1 Lake Park',
    tags: ['cool', 'teacher'],
  },
];

export default {
  data() {
    return {
      data,
      columns,
    };
  },
  methods: {
    log() {
      console.log('log');
    },
  },
};
</script>
