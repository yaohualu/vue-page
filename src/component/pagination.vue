<template>
  <div class="pagination">
    <ul>
      <li>总共100条数据</li>
      <li>
        <button>
          首页
        </button>  
      </li>
      <li>
        <button @click="goPage(--currentPage)" :disabled="currentPage === 1">
          上一页
        </button>
      </li>
      <li v-for="index in pages" :key="index">
        <button @click="goPage(index)" :class="{'active': currentPage === index}">
          {{index}}
        </button>
      </li>
      <li>
        <button @click="goPage(++currentPage)">
          下一页
        </button>
      </li>
      <li>
        <button>
          末页
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'pagination',
  data: function () {
    return {
      showItem: 5,
      allpage: 10,
      currentPage: 1
    }
  },
  computed: {
    pages: function () {
      let pages = [];
      if (this.currentPage < this.showItem) {
        let i = Math.min(this.showItem, this.allpage);
        while (i) {
          pages.unshift(i--);
        }
      } else {
        let middle = this.currentPage -Math.floor(this.showItem / 2);
        let i = this.showItem;
        if (middle > (this.allpage - this.showItem)) {
          middle = this.allpage - this.showItem + 1
        }
        while (i--) {
          pages.push(middle++);
        }
      }
      return pages;
    }
  },
  methods: {
    goPage: function (index) {
      this.currentPage = index;
    }
  }
}
</script>

<style>
  .pagination {
    text-align: center;
  }
  .pagination > ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }
  .pagination > ul > li {
    display: inline-block;
    margin: 0 2px;
  }
  .pagination > ul > li > button {
    border-radius: 4px;
    background: #fff;
    color: #000;
    border: 1px solid #ddd;
    padding: 5px 10px;
    cursor: pointer;
    font-size: 14px;
  }
  .pagination > ul > li > button:hover {
    background: #20A0FF;
    color: #fff;
    border: 1px solid #20A0FF;
  }
  .pagination > ul > li > button.active {
    background: #20A0FF;
    color: #fff;
    border: 1px solid #20A0FF;
  }
</style>
