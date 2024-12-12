<template>
    <div class="post">
        <div class="post_header">
            <div class="profile" :style="{ backgroundImage: `url(${post.userImage})` }"></div>
            <div class="profile_name">{{ post.name }}</div>
        </div>
        <div class="post_body" :style="{ backgroundImage: `url(${post.postImage})` }"></div>
        <div class="post_content">
            <p>{{ post.likes }} likes</p>
            <p>
                <strong>{{ post.name }}</strong
                >{{ post.content }}
            </p>
            <p class="date">{{ post.date }}</p>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Post',
    props: {
        post: Object
    }
};
</script>
<style>
.post {
    width: 100%;
}
.profile {
    background-image: url('https://cdn.pixabay.com/photo/2016/11/23/17/25/woman-1853939_1280.jpg');
    width: 30px;
    height: 30px;
    border-radius: 50%;
    background-size: 100%;
    float: left;
}
.profile_name {
    display: block;
    float: left;
    padding-left: 10px;
    padding-top: 10px;
    font-size: 14px;
}

.post_header {
    height: 30px;
    padding: 10px;
}

.post_body {
    height: 450px;
    background-image: url('https://media.istockphoto.com/id/1305950175/ko/사진/거대한-흑백-팬더가-대나무를-먹고-있습니다-큰-동물-클로즈업.jpg?s=2048x2048&w=is&k=20&c=szR7wqmitrgClcE6lfCghph5EgVmpydTqjacbSfrbR4=');
    background-position: center;
    background-size: cover;
}

.post_content {
    padding-left: 15px;
    padding-right: 15px;
    font-size: 14px;
}

.date {
    font-size: 11px;
    color: gray;
    margin-top: -8px;
}
</style>
