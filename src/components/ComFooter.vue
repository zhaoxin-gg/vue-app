<template>
  <footer :style="{ backgroundColor: curMenu.bgColor }">
    <div v-for="menu in menuList" 
    :key="menu.path"
    @click="switchMenu(menu)">
      <router-link :to="menu.path">{{ menu.name }}</router-link>
    </div>
  </footer>
</template>

<script>
import { mapState,mapMutations } from "vuex";
export default {
    computed: {
        ...mapState(['curMenu'])
    },
  data() {
    return {
      
      menuList: [
        { path: "/", name: "剧集", bgColor: "green" },
        { path: "/music", name: "音乐", bgColor: "#ff1232" },
        { path: "/book", name: "书籍", bgColor: "#ff00ff" },
        { path: "/chat", name: "聊天", bgColor: "#ffffff" },
      ],
    };
  },
  methods: {
      ...mapMutations(['setCurMenu']),
    switchMenu(menu) {
      this.setCurMenu(menu)
    },
  },
};
</script>

<style lang="scss" scoped>
footer {
  display: flex;
  justify-content: space-around;
  width: 100%;
  position: fixed;
  bottom: 0;
  height: 1rem;
  line-height: 1rem;
  text-align: center;
  background: red;
  span {
    position: absolute;
    left: 0;
  }
}
</style>