<template>
    <div>
        <Header></Header>
        <div id="myCarousel" class="carousel slide">
            <div class="carousel-inner">
                <div class="item active">
                <img src="./../assets/images/cartoon_banner.png" alt="First slide" style="width:100%">
                </div>
            </div>
        </div> 

        <section class="product_list_met_36_7_41 met-index-body best-room" m-id="41" id="showlist">
            <div class="container">
                <div class="best-room-carousel">
                    <ul class="best-room_ul no-space imagesize index-product-list tab-pane active animation-scale-up row">
                        <li class="best-room_li col-lg-4 col-md-4 col-sm-12" v-for="(item, index) in video_list" :key="index">
                            <div class="best-room_img">
                                <img :src="item.video_cover_pic" alt="" style="object-fit:cover">
                                <div class="best-room_overlay" @click="preview(item.video)">
                                    <div class="overlay_icn">
                                        <span></span>
                                    </div>
                                </div>
                            </div>
                        </li>

                    </ul>
                </div>
                <!-- 按钮 -->
                <!-- <a class="btn btn-brand pill" title="业务领域" target="_self">更多案例</a> -->
                <!-- /按钮 -->
            </div>
        </section>

        <div class="pop" v-if="pop_close">
            <div class="close_btn" @click="pop_close = false">关闭</div>
            <div class="poition_center" v-html="video"></div>
        </div>

        <img src="./../assets/images/tv_footer.png" style="width:100%;"/>
        <Footer></Footer>
    </div>
</template>

<script>
import Header from '@/components/Header'
import Footer from '@/components/Footer'
import list_data from '@/assets/json/huazhang_video_data.json'
    export default {
        components: {
            Header,
            Footer
        },
        data() {
            return {
                video_list: list_data.cartoon.concat(list_data.documentary),
                pop_close: false,
                video: ''
            }
        },
        methods: {
            preview(video) {
                console.log(video);
                this.pop_close = true;
                this.video = video;
            },
        }
    }
</script>

<style scoped>
.carousel {
    margin-top:70px !important;
}
.product_list_met_36_7_41 .best-room_img img {
    height:150px;
}
.product_h3 {
    cursor: pointer;
}
.pop {
    width:100%;
    height:100%;
    position: fixed;
    top:0;
    left:0;
    background: rgba(0,0,0,0.8);
    z-index:3000;
}
.close_btn {
    color:#fff;
    font-size:14px;
    float: right;
    margin:40px;
    cursor: pointer;
}
.poition_center {
    position: absolute;
    top:50%;
    left:50%;
    transform:translateX(-50%) translateY(-50%);
}
@media (max-width: 767px) {
    /deep/ iframe {
      width: 400px !important;
      height: 200px !important;
    } 
}
</style>