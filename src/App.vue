<template>
  <div id="app">
    <div class="np-category-select">
      <label for="cars">Choose a category:</label>
      <select
        @change="updateList()"
        name="category"
        id="category"
        class="np-category-select-input"
        v-model="selectedCategory"
      >
        <option value="All">All</option>
        <option value="Vegetable">Vegetable</option>
        <option value="Fruit">Fruit</option>
      </select>
    </div>

    <div class="np-list-item">
      <div class="np-ib np-ib-item np-ib-item__head">ID</div>
      <div class="np-ib np-ib-item np-ib-item__head">Title</div>
      <div class="np-ib np-ib-item np-ib-item__head">Category</div>
    </div>
    <div v-for="(item, i) in sortedListItems" :key="i" class="np-list-item">
      <div class="np-ib np-ib-item">
        {{ item.id }}
      </div>
      <div class="np-ib np-ib-item">
        {{ item.title }}
      </div>
      <div class="np-ib np-ib-item">
        {{ item.category }}
      </div>
    </div>
    <div class="np-credits">www.nightprogrammer.com</div>
  </div>
</template>

<script>
import { listItems } from "./listItems";

export default {
  name: "App",
  data() {
    return {
      listItems: listItems,
      sortedListItems: listItems,
      selectedCategory: "All",
    };
  },
  mounted() {
    this.sortedListItems = this.listItems;
  },
  methods: {
    updateList() {
      this.sortedListItems = [];
      this.sortedListItems =
        this.selectedCategory === "All"
          ? (this.sortedListItems = listItems)
          : listItems.filter((item) => item.category === this.selectedCategory);
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 12px 16px;
  max-width: 430px;
}
.np-list-item {
  border-bottom: 1px solid rgb(231, 231, 231);
}
.np-ib {
  display: inline-block;
}
.np-ib-item {
  min-width: 130px;
  padding: 6px;
}
.np-ib-item__head {
  font-weight: 600;
  color: #0059ff;
}
.np-category-select {
  margin: 4px 0px 20px 0px;
}
.np-category-select-input {
  min-width: 120px;
  margin-left: 10px;
  outline: none;
  border: 1px solid #0059ff;
  font-size: 16px;
  background: #0059ff;
  color: #ffffff;
  border-radius: 4px;
  padding: 3px;
}
.np-credits {
  font-size: 12px;
  margin-top: 12px;
}
</style>
