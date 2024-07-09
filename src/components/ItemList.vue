<template>
    <div class="item-list">
      <h1>Items</h1>
      <ul>
        <li v-for="item in items" :key="item.id" class="item">
          {{ item.name }}: {{ item.description }}
        </li>
      </ul>
    </div>
</template>
  
<script>
  import axios from 'axios';
  
  export default {
    name: 'ItemList',
    data() {
      return {
        items: []
      };
    },
    created() {
      this.fetchItems();
    },
    methods: {
      async fetchItems() {
        try {
          const response = await axios.get('http://localhost:8000/api/items/');
          this.items = response.data;
        } catch (error) {
          console.error('Error fetching items:', error);
        }
      }
    }
  };
</script>
  
<style scoped>
  .item-list {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    font-family: 'Arial', sans-serif;
  }
  
  .item {
    list-style-type: none;
    margin-bottom: 10px;
    padding: 10px;
    background-color: #f0f0f0;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .item h1 {
    font-size: 24px;
    color: #a51b1b;
  }
</style>
  