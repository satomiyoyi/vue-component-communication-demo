<template>
    <div style="border: 2px solid blue;">
        <h2>this is {{name}}</h2>
        <!-- 父组件向子组件传递属性和方法 -->
        <son1 :fathersaiedtoson="fathersaiedtoson1" @sonsaiedtofather = "sonsaiedtofather"
            v-bind="$attrs" v-on="$listeners"></son1>
        <!-- $attrs 和 $listeners 在次数使用不可以使用:和@ 作为过渡将祖先属性和方法传给儿子-->
        <son2 :fathersaiedtoson="fathersaiedtoson2" @sonsaiedtofather = "sonsaiedtofather"></son2>
        <div>son1 said: {{son1content}} <br> son2 said: {{son2content}} </div>
        <div>get son2 attribute : {{son2attribute}}</div>
    </div>
</template>
<script>
import son1 from './Son1';
import son2 from './Son2';
export default {
    data() {
        return {
            name: 'father',
            son1content: '',
            son2content: '',
            fathersaiedtoson1: 'hello son1 im father',
            fathersaiedtoson2: 'hello son2 im father',
            son2attribute: ''
        };
    },
    components: {
        son1,
        son2
    },
    methods: {
        sonsaiedtofather(name, content) {
            this[name + 'content'] = content;
        }
    },
    mounted() {
        // this.$children的获取只能在mounted之后
        this.son2attribute = this.$children[1].name;
    }
}
</script>