<template>
  <div>
    <div>Todo</div>
    <div>{{ items.length }} tasks remain</div>
    <div v-for="item in items" :key="item.name">
      <div>
        <div>
          name: {{ item.name }} | deadline: {{ item.deadline }}
          <button @click="deleteItem(item.name)">del</button>
        </div>
      </div>
    </div>
    <div>
      name
      <input type="text" v-model="newItemName" />
      deadline
      <input type="text" v-model="newItemDeadline" />
      <button @click="addItem">add</button>
    </div>
    <div>
      <button @click="backOperation">back</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  data() {
    return {
      newItemName: "",
      newItemDeadline: "??/??",
      delItemName: "delete",
      items: [
        { name: "first", deadline: "xx/xx" },
        { name: "second", deadline: "yy/yy" },
      ],
      deletedItems: [],
    };
  },
  methods: {
    addItem() {
      if (this.newItemName == "") return;
      this.items.push({
        name: this.newItemName,
        deadline: this.newItemDeadline,
      });
      this.newItemName = "";
      this.newItemDeadline = "??/??";
    },
    deleteItem(itemName) {
      this.items
        .filter((item) => item.name == itemName)
        .forEach((item) => this.deletedItems.push(item));
      this.items = this.items.filter((item) => item.name != itemName);
    },
    backOperation() {
      if (this.deletedItems.length == 0) return;
      this.items.push(this.deletedItems.pop());
    },
  },
};
</script>

<style></style>
