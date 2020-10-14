<template>
    <div class="flex justify-around box">
        <div
            @click="onClick_1"
            :data-url="item.url"
            :key="item.index"
            v-for="(item, index) in data"
        >
            <div class="flex bd">
                <image
                    class="layer"
                    src="https://img.alicdn.com/tfs/TB1bLoWoYH1gK0jSZFwXXc7aXXa-684-684.png"
                />
                <image class="bg" :src="item.coverImage" />
                <div class="flex align-center wrap">
                    <image
                        class="riverdinwei"
                        src="https://img.alicdn.com/tfs/TB1mtZRoVT7gK0jSZFpXXaTkpXa-28-36.png"
                    />
                    <text class="distance">距离500m</text>
                </div>
            </div>
            <div class="flex justify-center main">
                <text class="title">{{ item.title }}</text>
            </div>
            <div class="flex align-center justify-between ft">
                <div class="flex align-center block">
                    <image
                        class="xianjin"
                        src="https://img.alicdn.com/tfs/TB1OvsYoW61gK0jSZFlXXXDKFXa-60-60.png"
                    />
                    <text class="fashionHome">{{ item.user.userName }}</text>
                </div>
                <div
                    v-if="isReadCountShow(item.readCount)"
                    class="flex align-center group"
                >
                    <image
                        class="favorite"
                        src="https://img.alicdn.com/tfs/TB1arwYo7T2gK0jSZFkXXcIQFXa-46-44.png"
                    />
                    <text class="num">{{ item.readCount }}</text>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { fetch } from 'whatwg-fetch';
import jsonp from 'fetch-jsonp';
export default {
    data() {
        return {
            data: [
                {
                    title: '小户型卫浴怎样才能装得高大上？',
                    coverImage:
                        'https://img.alicdn.com/tfs/TB1Txq6o7T2gK0jSZFkXXcIQFXa-684-684.png',
                    readCount: 200,
                    user: {
                        userImage:
                            'https://img.alicdn.com/tfs/TB1DWe6oYj1gK0jSZFOXXc7GpXa-60-60.png',
                        userName: '时尚家居'
                    },
                    url: 'https://www.imgcook.com'
                },
                {
                    title: '拥有超多功能的40平米简约小公寓了解一下',
                    coverImage:
                        'https://img.alicdn.com/tfs/TB1XRQTo7P2gK0jSZPxXXacQpXa-684-648.png',
                    readCount: 500,
                    user: {
                        userImage:
                            'https://img.alicdn.com/tfs/TB1DWe6oYj1gK0jSZFOXXc7GpXa-60-60.png',
                        userName: '花花设计工作'
                    },
                    url: 'https://www.imgcook.com/docs'
                }
            ],
            constants: {}
        };
    },
    methods: {
        isReadCountShow(readCount) {
            return readCount > 300;
        },
        fetch_example() {
            fetch('https://jsonplaceholder.typicode.com/todos/1', {
                method: 'GET',
                headers: '{"Content-Type":"json"}'
            })
                .then(response => response.json())
                .then((data, error) => {
                    console.log('fetch example: ', data, error);
                    return data;
                })
                .catch(e => {
                    console.log('error', e);
                });
        },
        jsonp_example() {
            jsonp('https://assets.airbnb.com/frontend/search_results.js', {
                jsonpCallbackFunction: 'search_results',
                body: {}
            })
                .then(response => response.json())
                .then((data, error) => {
                    console.log('jsonp example: ', data, error);
                    return data;
                })
                .catch(e => {
                    console.log('error', e);
                });
        },
        onClick_1(e) {
            window.open(this.item.url, '_blank');
        }
    },
    created() {
        console.log('super props');
        this.fetch_example();
        this.jsonp_example();
    },
    updated() {}
};
</script>
<style scoped lang="scss">
@import './index.rpx.scss';
</style>
