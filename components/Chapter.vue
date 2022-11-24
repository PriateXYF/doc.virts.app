<template>
  <div>
    <div v-for="(item, index) in chapters" :key="index">
      <el-divider class="card-divider" content-position="left">{{item.category}}</el-divider>
      <el-row class="allcard">
        <el-col :xs="24" :sm="12" :md="8" :lg="6" :xl="4" v-for="(chapter, index) in item.chapters" :key="index">
          <el-card @click.native="toPage(chapter)" class="indexcontainer card" :class="chapter.isBlock && 'block'">
            <div style="padding: 14px;">
              <span><i v-show="chapter.isBlock" class="el-icon-lock"></i>{{chapter.isBlock ? '' : chapter.name}}</span>
              <div class="bottom clearfix">
                <div class="desc">{{chapter.isBlock ? '已锁定' : chapter.desc}}</div>
              </div>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<style>
  .allcard {
    margin: 20px;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .indexcontainer {
    margin: 0 auto;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .card {
    margin: 10px;
    /* width: 100%; */
    background-size: cover !important;
    font-size: 30px;
  }

  .card:hover {
    cursor: pointer;
  }

  .el-divider__text {
    font-size: 30px;
  }

  .block {
    cursor: not-allowed !important;
  }

  .bottom {
    margin-top: 13px;
    font-size: 20px;
    line-height: 12px;
  }

</style>

<script>
  export default {
    props : ['chapters'],
    data() {
      return {
      }
    },
    methods: {
      pushTo(item) {
      },
      toPage(item) {
        !item.isBlock && window.open(`/${this.$route.params.docs}/${item.url}`, "_blank")
      }
    },
  }

</script>
