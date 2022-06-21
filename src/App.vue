<template>
  <div>
    <ul>
      <li v-for="(item, idx) in items" :key="idx">
        {{ item.name }} - {{ item.price }}
      </li>
    </ul>
    <button @click="addAndUpdate">Add and update</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      items: [
        { name: "Alph", price: 1 },
        { name: "Beta", price: 2 },
      ],
    };
  },

  methods: {
    addAndUpdate() {
      const newItem = { name: "New", price: "-" };
      this.items.push(newItem);
      setTimeout(() => {
        // каждый item представляет собой объект с геттерами/сеттерами
        console.log(this.items);
        newItem.price = "over 9000";

        // это то еще прокатит
        // this.items[0].foo = 'baz';

        // а вот так уже раньше не мог - теперь пофиксили. Ограничение реактивности из-за неудачной модели геттеров и сеттеров

        this.items[0] = { name: "WGrcghvjhg", price: 18990 };

        // правильно вот так
        // this.items[0].name = "WGrcghvjhg";
        // this.items[0].price = 18990;
      }, 3000);
    },
  },
};
</script>
