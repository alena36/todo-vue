<template>
    <div>
        <p>{{msg}}</p>
        <p>
            <button @click="addButtonClick"
                    :disabled="!userText"
                    class="button">{{btnAddLabel}}
            </button>
            <button @click="removeButtonClick"
                    :disabled="!info.length"
                    class="button">{{btnRemoveLabel}}
            </button>
        </p>
        <p>
            <input type="text" v-model="userText">
        </p>
        <div class="list">
            <ul>
                <li v-for="infoItem in info"
                    :key="infoItem.id">
                    {{infoItem.text}}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  name: 'my-component',
  props: ['msg'],
  data() {
    return {
      info: [
        { text: 'Текст1', id: 0 },
        { text: 'Текст2', id: 1 },
        { text: 'Текст3', id: 2 },
      ],
      userText: '',
      btnAddLabel: 'Добавить',
      btnRemoveLabel: 'Удалить',
    };
  },
  watch: {
    userText(value) {
      if (value === '123') {
        this.userText = '-';
      }
    },
  },
  methods: {
    addButtonClick() {
      this.info.push({ text: this.userText });
      this.userText = '';
    },
    removeButtonClick() {
      this.info.shift();
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .list {
        padding: 5px;
        border: 1px solid lightgrey;
    }
    .button {
        font-size: 16px;
    }
</style>
