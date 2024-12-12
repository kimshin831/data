<template>
    <div class="header">
        <ul class="header-button-left">
            <li>Cancel</li>
        </ul>
        <ul class="header-button-right">
            <li>Next</li>
            <!-- steop2에서만 보여져야 함. 발행을 클릭하면 함수실행.-->
        </ul>
        <img src="./assets/logo.png" class="logo" />
    </div>

    <!-- props로 전달하는 방법 :보내고 = “” 등록하고 쓰고 -->
    <Container :post="post" />

    <!-- 더보기 버튼 -->
    <div v-if="!noMoreData">
        <button @click="more">더보기</button>
    </div>
    <div v-else>
        <p>더 이상 이미지가 없습니다.</p>
    </div>
    <!-- 3번 -->

    <div class="footer">
        <ul class="footer-button-plus">
            <input type="file" id="file" class="inputfile" />
            <label for="file" class="input-plus">+</label>
        </ul>
    </div>
</template>

<script>
import Container from './components/Container.vue'; /* 1번 */
import postdata from './assets/postdata.js';
/* axios로 ajax요청하기 */
import axios from 'axios';
/* axios.get()  */ // 내가원하는 url로 get요청할 수 있음.

export default {
    name: 'App',
    data() {
        return {
            post: postdata /* Post.vue에 전송 */,
            더보기: 0,
            noMoreData: false // 데이터가 더이상 없음을 나타내는 상태
        };
    },
    components: {
        Container: Container /* 2번 */
    },
    methods: {
        more() {
            // 더보기 카운트가 2이상이면 데이터를 요청하지 않도록
            if (this.더보기 >= 2) {
                this.noMoreData = true;
                return;
            }

            axios
                .get(`https://jellyzoo.github.io/data/vuemore${this.더보기}.json`)
                .then((결과) => {
                    this.post.push(결과.data); // 새로운 데이터 추가
                    this.더보기++;
                })
                .catch(() => {
                    // 요청에 실패시 데이터를 더이상 불러올 수 없도록 처리
                    this.noMoreData = true;
                });
        }
    }
};
</script>

<style>
@import './css/style.css';
</style>
