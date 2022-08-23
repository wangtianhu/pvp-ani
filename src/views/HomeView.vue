<template>
  <div class="transition-wrapper">
    <div class="transition-content">
      <p>动画显示</p>
      <div class="ani-wrapper">
        <div class="ani-detail" v-if="isShowAni">
          <!-- <div class="ani-obj"></div> -->
          <div class="tabs">
            <p
              v-for="({ name, chose }, index) in tabsList"
              @click="handleChose(index)"
              :class="{ active: chose }"
              :key="index"
            >
              {{ name }}
            </p>
          </div>
        </div>
        <div class="code" v-else>
          <pre><code>
          .sss{
            width:200px;
          }
          </code></pre>
        </div>
      </div>
    </div>
    <div class="transition-types">
      <p class="type">按钮动画</p>
      <div class="types-list">
        <p v-for="item in btnAniList" :key="item">{{ item }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "transition",
  data() {
    return {
      isShowAni: true,
      btnAniList: ["hover", "click"],
      tabsList: [
        {
          name: "直播",
          chose: true,
        },
        {
          name: "活动中心",
          chose: false,
        },
        {
          name: "个人设置",
          chose: false,
        },
      ],
    }
  },
  methods: {
    handleChose(index) {
      this.tabsList.forEach((v) => (v.chose = false))
      this.tabsList[index].chose = true
    },
  },
}
</script>

<style lang="scss" scoped>
.transition-wrapper {
  width: 962px;
  height: 560px;
  background: #fff;
  position: fixed;
  top: 50%;
  left: 50%;
  border-radius: 5px;
  transform: translate(-50%, -50%);
  border: 1px solid #eaeefb;
  box-shadow: 0 6px 18px 0 rgb(232 237 250 / 50%);
  z-index: 33;
  display: flex;
  justify-content: center;
  align-items: center;
  .transition-content {
    width: 600px;
    height: 100%;
    border-right: 1px solid #eaeefb;
    padding: 30px;
    .ani-wrapper {
      width: 100%;
      height: 100%;
      .ani-detail {
        width: 100%;
        height: 100%;
        position: relative;
        .ani-obj {
          background: #48b1ff;
          width: 80px;
          height: 80px;
          border-radius: 5px;
          position: absolute;
          left: 50%;
          top: 50%;
          transform: translate(-50%, -50%);
        }
        .tabs {
          display: flex;
          justify-content: center;
          align-items: center;
          p {
            display: inline-block;
            height: 40px;
            max-width: 120px;
            min-width: 100px;
            font-size: 16px;
            color: #9c9c9c;
            transition: all 0.3s ease;
            margin-left: 20px;
            cursor: pointer;
            position: relative;
            &::after {
              content: "";
              width: 0;
              height: 3px;
              background: #48b1ff;
              position: absolute;
              left: 50%;
              transform: translateX(-50%);
              bottom: -8px;
              transition: all 0.3s ease;
            }
            &:hover {
              color: #8988ff;
              font-size: 18px;
              &::after {
                width: 100%;
              }
            }
            &.active {
              color: #48b1ff;
              font-size: 18px;
              &::after {
                width: 100%;
              }
            }
          }
        }
      }
    }
  }
  .transition-types {
    flex: 1;
    padding: 20px;
    .type {
      color: #99a9bf;
      font-size: 14px;
      font-weight: 500;
      margin-bottom: 15px;
    }
    .types-list {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      > p {
        width: 45%;
        height: 40px;
        line-height: 40px;
        font-size: 12px;
        color: #99a2bf;
        background: #eaeefb;
        border-radius: 5px;
        cursor: pointer;
        transition: all 0.3s ease;
        &:hover {
          background: #48b1ff;
          color: #fff;
        }
      }
    }
  }
}
</style>
