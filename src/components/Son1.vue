<template>
    <div style="border: 1px solid green;">
        <h3>this is {{name}}</h3>
        <button @click="saied">saied</button>
        <div>grandpa saied : {{this.grandsaidtograndson}}</div>
        <div>father saied : {{this.fathersaiedtoson}}</div>
        <div>get father attribute : {{fathername}}</div>
        <div>brother saied:{{brothersaied}}</div>
    </div>
</template>
<script>
// 兄弟通信使用了eventBus
import bus from './EventBus';
export default {
    props: {
        fathersaiedtoson: {
            type: String
        },
        grandsaidtograndson: {
            type: String
        }
    },
    data() {
        return {
            name: 'son1',
            brothersaied: '',
            fathername: this.$parent.name
        };
    },
    methods: {
        saied() {
            this.$emit('sonsaiedtofather', 'son1', 'hello im son1');
            this.$emit('grandsonsaidtograndpa', 'son1', 'hello im son1');
        }
    },
    beforeMount() {
        // 利用bus向其他组件传递信息
        // 使用箭头函数 避免this指向bus
        bus.$on('brother1saied', msg => {
            this.brothersaied = msg;
        });
    },
    mounted() {
        bus.$emit('brother2saied', 'brother2 im ready');
    }
}
</script>