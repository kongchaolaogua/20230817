<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <button v-on:click="changeCount">{{ count }}</button>
        <p>{{ count.toFixed(2) }}</p>
        <p>{{ str.toLocaleLowerCase() }}</p>
        <p v-bind:class="color" v-bind:style="s">str.toLocaleLowerCase()</p>
        <ul v-html="li">

        </ul>

        <div>
            <input type="radio" name="sex" v-on:click="danger = 1" :checked="danger == 1">男
            <input type="radio" name="sex" v-on:click="danger = 0" :checked="danger == 0">女
        </div>
        <br />
        <div>
            <div v-if="danger == 1">♂ 男 {{ danger }}</div>
            <div v-if="danger == 0">♀ 女 {{ danger }}</div>
        </div>
        <!-- 考试成绩评定 -->
        <div>考试成绩为：{{ cj }}</div>




        <div>
            <span v-if="cj>90">
                成绩评分A,.....
            </span>
            <span v-else-if="cj>80">
                成绩评分B,.....
            </span>
            <span v-else-if="cj>70">
                成绩评分C,.....
            </span>
            <span v-else>
                成绩评分D,.....
            </span>
        </div>

        <h1>点击按钮换图</h1>
        <h2>
            <button v-on:click="tapBanner(0)">上一页</button>
            <span>{{ rotation[rotationIndex].name }}</span>
            <button v-on:click="tapBanner(1)">下一页</button>
        </h2>

        <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    props: {},
    data() {
        return {
            color: "red",
            str: 'this is a new vue product',
            s: "color:white;height:40px;background-color:black;line-height:40px",
            count: 0,
            msg: "当前页面是组件页面，项目通过vue create创建",
            li: "<li>这是一个li标签</li>",
            danger: 0,
            cj: 1,
            rotationIndex:0,
            rotation:[
                {id:1,"name":"波仔1","img":"1.jpg"},
                {id:2,"name":"波仔2","img":"2.jpg"},
                {id:3,"name":"波仔3","img":"3.jpg"},
                {id:4,"name":"波仔4","img":"4.jpg"},
                {id:5,"name":"波仔5","img":"5.jpg"},
                {id:6,"name":"波仔6","img":"6.jpg"},
            ]
        }
    },
    methods: {
        tapBanner(who){
            if(who){
                this.rotationIndex++
                if( this.rotationIndex >= this.rotation.length - 1){
                    this.rotationIndex = 0
                }
                
            }else{
                this.rotationIndex--
                if( this.rotationIndex <= 0){
                    this.rotationIndex = this.rotation.length - 1
                }
                
            }
        },
        changeCount() {
            this.count += 5
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
