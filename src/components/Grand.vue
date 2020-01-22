<template>
    <div style="border: 3px solid red; width: 300px">
        <h1>this is {{name}}</h1>
        <div>grand son said: {{grandsonsaid}}</div>
        <!-- 向孙子组件传递属性和方法 -->
        <father :grandsaidtograndson="grandsaidtograndson" @grandsonsaidtograndpa="grandsonsaidtograndpa"></father>
    </div>
</template>
<script>
import father from './Father';
export default {
    data() {
        return {
            name: 'grand',
            grandsaidtograndson: 'hello boy im grandpa',
            grandsonsaid: ''
        };
    },
    provide() {
        return {
            grandson2saidtograndpa: this.grandsonsaidtograndpa
        };
    },
    components: {
        father
    },
    methods: {
        grandsonsaidtograndpa(name, content) {
            this.grandsonsaid = content;
        }
    }
};
</script>